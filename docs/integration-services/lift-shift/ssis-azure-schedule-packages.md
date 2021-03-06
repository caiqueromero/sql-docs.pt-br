---
title: Agendar pacote SSIS no Azure | Microsoft Docs
ms.date: 05/09/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4bfad00425848189d88bd780296db00ec810b37c
ms.sourcegitcommit: 0cc2cb281e467a13a76174e0d9afbdcf4ccddc29
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="schedule-the-execution-of-an-ssis-package-in-azure"></a>Agendar a execução de um pacote SSIS no Azure
Você pode agendar a execução de pacotes armazenados no banco de dados de catálogo do SSISDB em um servidor de Banco de Dados SQL do Azure, escolhendo uma das seguintes opções de agendamento:
-   [A opção Agendar no SSMS (SQL Server Management Studio)](#ssms)
-   [A atividade Executar Pacote SSIS do Azure Data Factory](#execute)
-   [A atividade de procedimento armazenado do Azure Data Factory SQL Server](#storedproc)
-   [Trabalhos Elásticos de Banco de Dados SQL](#elastic)
-   [SQL Server Agent](#agent)

## <a name="ssms"></a> Agendar um pacote com o SSMS

No SSMS (SQL Server Management Studio), é possível clicar com o botão direito do mouse em um pacote implantado no banco de dados do Catálogo do SSIS, SSISDB, e selecionar **Agendar** para abrir a caixa de diálogo **Nova agenda**. Para saber mais, confira [Agendar a execução de um pacote SSIS no Azure com SSMS](ssis-azure-schedule-packages-ssms.md).

Esse recurso exige o SQL Server Management Studio versão 17.7 ou superior. Para obter a versão mais recente do SSMS, confira [Fazer o download do SSMS (SQL Server Management Studio)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="execute"></a> Agendar um pacote com a atividade Executar pacote SSIS

Para obter informações sobre como agendar um pacote do SSIS usando a atividade Executar pacote do SSIS no Azure Data Factory, consulte [Executar um pacote SSIS usando a atividade do SSIS no Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

## <a name="storedproc"></a> Agendar um pacote com a atividade Procedimento armazenado

Para obter informações sobre como agendar um pacote do SSIS usando a atividade de Procedimento Armazenado no Azure Data Factory, consulte [Executar um pacote SSIS usando a Atividade de Procedimento Armazenado no Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity).

Para o Data Factory versão 1, consulte [Executar um pacote SSIS usando a atividade de Procedimento Armazenado no Azure Data Factory](https://docs.microsoft.com/azure/data-factory/v1/how-to-invoke-ssis-package-stored-procedure-activity).

## <a name="elastic"></a> Agendar um pacote com trabalhos elásticos de Banco de Dados SQL

Para obter mais informações sobre trabalhos elásticos no Banco de Dados SQL, consulte [Gerenciando bancos de dados de nuvem expandidos](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Prerequisites

Antes que você possa usar trabalhos elásticos para agendar pacotes do SSIS armazenados no banco de dados de catálogo do SSISDB em um servidor de Banco de Dados SQL do Azure, você deverá fazer o seguinte:

1.  Instale e configure os componentes de trabalhos de banco de dados elástico. Para obter mais informações, consulte [Visão geral da instalação de trabalhos de Banco de Dados Elástico](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Crie credenciais no escopo do banco de dados que os trabalhos possam usar para enviar comandos para o banco de dados de catálogo do SSIS. Para obter mais informações, veja [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Criar um trabalho elástico

Crie o trabalho usando um script Transact-SQL semelhante ao mostrado no exemplo a seguir:

```sql
-- Create Elastic Jobs target group 
EXEC jobs.sp_add_target_group 'TargetGroup' 

-- Add Elastic Jobs target group member 
EXEC jobs.sp_add_target_group_member @target_group_name='TargetGroup', 
    @target_type='SqlDatabase', @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB' 

-- Add a job to schedule SSIS package execution
EXEC jobs.sp_add_job @job_name='ExecutePackageJob', @description='Description', 
    @schedule_interval_type='Minutes', @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXEC jobs.sp_add_jobstep @job_name='ExecutePackageJob', 
    @command=N'DECLARE @exe_id bigint 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runinscaleout=1, @useanyworker=1, 
            @execution_id=@exe_id OUTPUT         
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0', 
    @credential_name='YourDBScopedCredentials', 
    @target_group_name='TargetGroup' 

-- Enable the job schedule 
EXEC jobs.sp_update_job @job_name='ExecutePackageJob', @enabled=1, 
    @schedule_interval_type='Minutes', @schedule_interval_count=60 
```

## <a name="agent"></a> Agendar um pacote com o SQL Server Agent

### <a name="prerequisite---create-a-linked-server"></a>Pré-requisito – criar um servidor vinculado

Antes de usar o SQL Server Agent local para agendar a execução de pacotes armazenados em um servidor de Banco de Dados SQL do Azure, você precisa adicionar o servidor de Banco de Dados SQL ao seu SQL Server local como um servidor vinculado.

1.  **Configurar o servidor vinculado**

    ```sql
    -- Add the SSISDB database on your Azure SQL Database as a linked server to your SQL Server on premises
    EXEC sp_addlinkedserver
        @server='myLinkedServer', -- Name your linked server
        @srvproduct='',     
        @provider='sqlncli', -- Use SQL Server native client
        @datasrc='<server_name>.database.windows.net', -- Add your Azure SQL Database server endpoint
        @location=‘’,
        @provstr=‘’,
        @catalog='SSISDB'  -- Add SSISDB as the initial catalog
    ```

2.  **Configurar as credenciais do servidor vinculado**

    ```sql
    -- Add your Azure SQL DB server admin credentials
    EXEC sp_addlinkedsrvlogin
        @rmtsrvname = 'myLinkedServer’,
        @useself = 'false’,
        @rmtuser = 'myUsername', -- Add your server admin username
        @rmtpassword = 'myPassword' -- Add your server admin password
    ```

3.  **Configurar as opções do servidor vinculado**

    ```sql
    EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;
    ```

Para obter mais informações, consulte [Criar servidores vinculados](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) e [Servidores vinculados](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Criar um trabalho do SQL Server Agent

Para agendar um pacote com o SQL Server Agent local, crie um trabalho com uma etapa de trabalho que chama os procedimentos armazenados do catálogo SSIS `[catalog].[create_execution]` e depois `[catalog].[start_execution]`. Para obter mais informações, consulte [Trabalhos do SQL Server Agent para pacotes](../packages/sql-server-agent-jobs-for-packages.md).

1.  No SQL Server Management Studio, conecte-se ao banco de dados do SQL Server local no qual você deseja criar o trabalho.

2.  Clique com o botão direito do mouse no nó **SQL Server Agent**, selecione **Novo** e, em seguida, selecione **Trabalho** para abrir a caixa de diálogo **Novo Trabalho**.

3.  Na caixa de diálogo **Novo Trabalho**, selecione a página **Etapas** e, em seguida, selecione **Novo** para abrir a caixa de diálogo **Nova Etapa do Trabalho**.

4.  Na caixa de diálogo **Nova Etapa do Trabalho**, selecione `SSISDB` como o **Banco de dados**.

5.  No campo **Comando**, insira um script do Transact-SQL semelhante ao mostrado no exemplo a seguir:

    ```sql
    -- T-SQL script to create and start SSIS package execution using SSISDB stored procedures
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
        @folder_name=N'folderName', @project_name=N'projectName', 
        @package_name=N'packageName', @use32bitruntime=0, @runincluster=1, @useanyworker=1,
        @execution_id=@exe_id OUTPUT 

    EXEC [YourLinkedServer].[SSISDB].[catalog].[set_execution_parameter_value] @exe_id,
        @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id
    ```

6.  Conclua a configuração e o agendamento do trabalho.

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o SQL Server Agent, consulte [Trabalhos do SQL Server Agent para pacotes](../packages/sql-server-agent-jobs-for-packages.md).

Para obter mais informações sobre trabalhos elásticos no Banco de Dados SQL, consulte [Gerenciando bancos de dados de nuvem expandidos](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).
