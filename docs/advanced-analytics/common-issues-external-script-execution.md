---
title: Problemas comuns com o serviço barra inicial e a execução do script externo no SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 08ab6e2db6d6cde5e41f7ddb88c8afd1da241df7
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34706834"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Problemas comuns com o serviço barra inicial e a execução do script externo no SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 Serviço Launchpad confiável do SQL Server dá suporte à execução de script externo para R e Python. No SQL Server 2016 R Services SP1 fornece o serviço. SQL Server 2017 inclui Nom a barra inicial como parte da instalação inicial.

Vários problemas podem impedir que a barra inicial de início, incluindo problemas de configuração ou as alterações ou falta de protocolos de rede. Este artigo fornece orientação para solução de problemas para muitos problemas. Para qualquer são perdidos, você poderá postar perguntas para o [Fórum do servidor de aprendizado de máquina](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR).

**Aplica-se a:** R Services do SQL Server 2016, SQL Server 2017 serviços de aprendizado de máquina

## <a name="determine-whether-launchpad-is-running"></a>Determinar se a barra inicial está em execução

1. Abra o **serviços** painel (Services.msc). Ou, na linha de comando, digite **SQLServerManager13.msc** ou **SQLServerManager14.msc** abrir [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Anote a conta de serviço barra inicial está sendo executado. Cada instância em que R ou Python é habilitado deve ter sua própria instância do serviço Launchpad. Por exemplo, o serviço para uma instância nomeada pode ser algo como _MSSQLLaunchpad$ InstanceName_.

3. Se o serviço for interrompido, reinicie-o. Na reinicialização, se houver algum problema com a configuração, uma mensagem é publicada no log de eventos do sistema e o serviço for interrompido novamente. Verifique o log de eventos do sistema para obter detalhes sobre por que o serviço foi interrompido.

4. Examine o conteúdo do RSetup.log e certifique-se de que não há nenhum erro na instalação. Por exemplo, a mensagem *saindo com código 0* indica falha do serviço de inicialização.

5. Para procurar por outros erros, examine o conteúdo do rlauncher.log.

## <a name="check-the-launchpad-service-account"></a>Verificar a conta de serviço barra inicial

A conta de serviço padrão pode ser "NT Service\$SQL2016" ou "serviço NT\$SQL2017". A parte final pode variar, dependendo de seu nome de instância do SQL.

O serviço Launchpad (Launchpad.exe) é executado usando uma conta de serviço de baixo privilégio. No entanto, para iniciar o R e Python e se comunicar com a instância de banco de dados, a conta de serviço do Launchpad requer os seguintes direitos de usuário:

- Fazer logon como um serviço (SeServiceLogonRight)
- Substituir um token de nível de processo (SeAssignPrimaryTokenPrivilege)
- Ignorar verificação completa (SeChangeNotifyPrivilege)
- Ajustar quotas de memória para um processo (SeIncreaseQuotaPrivilege)

Para obter informações sobre esses direitos de usuário, consulte a seção "Windows privilégios e direitos de" [permissões e contas de serviço do Windows configurar](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Se você estiver familiarizado com o uso da ferramenta de diagnóstico de suporte à plataforma (SDP) para diagnóstico do SQL Server, você pode usar SDP examine o arquivo de saída com o nome MachineName_UserRights.txt.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Grupo de usuários para a barra inicial não é possível fazer logon localmente

Durante a instalação dos serviços de aprendizado de máquina, o SQL Server cria o grupo de usuários do Windows **SQLRUserGroup** e configura com todos os direitos necessários para a barra inicial para se conectar ao SQL Server e executar tarefas de script externo. Se esse grupo de usuário estiver habilitado, ele também é usado para executar scripts de Python.

No entanto, em organizações onde mais restritivas políticas de segurança são aplicadas, os direitos necessários para este grupo podem ter sido removidos manualmente ou podem ser revogados automaticamente pela política. Se os direitos foram removidos, barra inicial não pode se conectar ao SQL Server e do SQL Server não é possível chamar o tempo de execução externo.

Para corrigir o problema, garanta que o **SQLRUserGroup** tenha o direito de sistema **Permitir logon local**.

Para obter mais informações, consulte [permissões e contas de serviço do Windows configurar](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

## <a name="permissions-to-run-external-scripts"></a>Permissões para executar scripts externos

Mesmo se a barra inicial é configurado corretamente, ele retornará um erro se o usuário não tem permissão para executar scripts R ou Python.

Se você instalou o SQL Server como um administrador de banco de dados ou é um proprietário de banco de dados, recebem automaticamente essa permissão. No entanto, outros usuários geralmente tem mais permissões limitadas. Se tentar executar um script de R, eles recebem um erro de barra inicial.

Para corrigir o problema, no SQL Server Management Studio, um administrador de segurança pode modificar o logon do SQL ou a conta de usuário do Windows, executando o script a seguir:

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Para obter mais informações, consulte [GRANT (Transact-SQL](../t-sql/statements/grant-transact-sql.md).

## <a name="common-launchpad-errors"></a>Erros comuns de barra inicial

Esta seção lista as mensagens de erro mais comuns que retorna da barra inicial.

## <a name="unable-to-launch-runtime-for-r-script"></a>"Não é possível iniciar o tempo de execução de script R"

Se o grupo do Windows para usuários de R (também usada para Python) não pode fazer logon para a instância que está executando serviços de R, você poderá ver os seguintes erros:

- Erros gerados quando você tentar executar scripts R:

    * *Não é possível iniciar o tempo de execução para o script do “R”. Verifique a configuração do tempo de execução do script do R.*

    * *Erro de script externo. Não é possível iniciar o tempo de execução.*

- Erros gerados pelo [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] serviço:

    * *Falha ao inicializar o inicializador RLauncher.dll*

    * *Nenhuma dll do inicializador foi registrada!*

    * *Logs de segurança indicam que a conta de serviço do NT não pôde fazer logon*

Para obter informações sobre como conceder as permissões necessárias a este grupo de usuário, consulte [instalar o SQL Server 2016 R Services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Essa limitação não se aplicará se você usar logons SQL para executar scripts do R em uma estação de trabalho remota.

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>"Falha de logon: o usuário não recebeu o tipo de logon solicitado"

Por padrão, [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] usa a seguinte conta durante a inicialização: `NT Service\MSSQLLaunchpad`. A conta é configurada por [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] instalação tenha todas as permissões necessárias.

Se você atribuir uma conta diferente para a barra inicial ou à direita é removida por uma política de computador do SQL Server, a conta pode não ter as permissões necessárias, e você poderá ver esse erro:

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Falha de logon: o usuário não recebeu o tipo de logon solicitado neste computador.*

Para conceder as permissões necessárias para a nova conta de serviço, use o aplicativo de diretiva de segurança Local e atualizar as permissões da conta para incluir as seguintes permissões:

+ Ajustar cotas de memória para um processo (SeIncreaseQuotaPrivilege)
+ Ignorar verificação completa (SeChangeNotifyPrivilege)
+ Fazer logon como um serviço (SeServiceLogonRight)
+ Substituir um token de nível de processo (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>"Não é possível se comunicar com o serviço barra inicial"

Se você tiver instalado e, então, aprendizado de máquina, mas você receberá esse erro ao tentar executar um script R ou Python, o serviço barra inicial para a instância pode ter parado em execução.

1. Em um prompt de comando do Windows, abra o SQL Server Configuration Manager. Para obter mais informações, consulte [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Launchpad do SQL Server para a instância e, em seguida, selecione **propriedades**.

3. Selecione o **Service** guia e, em seguida, verifique se o serviço está em execução. Se não estiver em execução, altere o **modo inicial** para **automático**e, em seguida, selecione **aplicar**.

4. Reiniciar o serviço geralmente corrige o problema para que podem executar scripts de aprendizado de máquina. Se a reinicialização não resolver o problema, observe o caminho e argumentos no **caminho binário** propriedade e faça o seguinte:

    A. Examine o arquivo. config do iniciador e verifique se o diretório de trabalho é válido.

    B. Certifique-se de que o grupo do Windows que é usado pela barra inicial pode se conectar à instância do SQL Server, conforme descrito no [seção anterior](#bkmk_LaunchpadTS).

    c. Se você alterar qualquer uma das propriedades do serviço, reinicie o serviço Launchpad.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>"Falha na criação de erro fatal de tmpFile"

Nesse cenário, você instalou com êxito os recursos de aprendizado de máquina e barra inicial está em execução. Você tenta executar um código de R ou Python simples, mas Launchpad falhará com um erro semelhante ao seguinte: 

>*Não é possível se comunicar com o tempo de execução de script R. Verifique os requisitos de tempo de execução de R.*

Ao mesmo tempo, o tempo de execução do script externo grava a mensagem a seguir como parte da mensagem STDERR: 

>*Erro fatal: criação de tmpfile falhou.*

Esse erro indica que a conta que a barra inicial está tentando usar não tem permissão para fazer logon no banco de dados. Essa situação pode ocorrer quando as políticas de segurança estrita são implementadas. Para determinar se esse for o caso, verifique os logs do SQL Server e para ver se a conta MSSQLSERVER01 foi negada no logon. As mesmas informações são fornecidas nos logs que são específicos para R\_serviços ou PYTHON\_serviços. Procure ExtLaunchError.log.

Por padrão, 20 contas são configuradas e associadas ao processo de Launchpad.exe, com os nomes MSSQLSERVER01 por meio de MSSQLSERVER20. Se você fizer um uso intenso do R ou Python, você pode aumentar o número de contas.

Para resolver o problema, verifique se o grupo tem *permitir logon local* permissões para a instância do local onde os recursos de aprendizado de máquina foi instalados e habilitados. Em alguns ambientes, este nível de permissão pode precisar de uma exceção de GPO do administrador de rede.

## <a name="not-enough-quota-to-process-this-command"></a>"Não há cota suficiente para processar este comando"

Esse erro pode significar várias coisas:

- Barra inicial pode ter usuários externos insuficientes para executar a consulta externa. Por exemplo, se você estiver executando mais de 20 consultas externas simultaneamente, e existem apenas 20 usuários padrão, uma ou mais consultas podem falhar.

- Memória disponível é insuficiente para processar a tarefa de R. Esse erro geralmente ocorre em um ambiente padrão, onde os SQL Server pode estar usando até 70% dos recursos do computador. Para obter informações sobre como modificar a configuração do servidor para dar suporte à maior uso de recursos por R, consulte [operacionalização do código R](r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>"Não é possível localizar o pacote"

Se você executa o código R no SQL Server e receber essa mensagem, mas não obteve a mensagem quando você executou o mesmo código fora do SQL Server, isso significa que o pacote não foi instalado no local padrão de biblioteca usado pelo SQL Server.

Esse erro pode ocorrer de várias maneiras:

- Você instalou um novo pacote no servidor, mas o acesso foi negado para que R instalado o pacote em uma biblioteca do usuário.

- Você instalou o R Services e, em seguida, outra ferramenta de R instalada ou conjunto de bibliotecas, incluindo Microsoft R Server (autônomo), Microsoft R Client, RStudio e assim por diante.

Para determinar o local da biblioteca de pacote de R que é usado pela instância, abra o SQL Server Management Studio (ou qualquer outra ferramenta de consulta de banco de dados), conecte-se à instância e, em seguida, execute o seguinte procedimento armazenado:

```SQL
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Resultados de exemplo

*Mensagem(ns) STDOUT do script externo:*

*[1] "c:\\arquivos de programa\\do Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES "*

*[1] "SQL de arquivos/Microsoft Server/MSSQL13 da unidade c: / programa. R_SERVICES/SQL2016/biblioteca"*

Para resolver o problema, você deverá reinstalar o pacote para a biblioteca de instância do SQL Server.

>[!NOTE]
>Se você tiver atualizado uma instância do SQL Server 2016 para usar a versão mais recente do Microsoft R, o local padrão da biblioteca é diferente. Para obter mais informações, consulte [SqlBindR de uso para atualizar uma instância dos serviços do R](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Barra inicial é desligado devido a DLLs incompatíveis

Se você instala o mecanismo de banco de dados com outros recursos, o servidor de patch e, em seguida, adicionar o recurso de aprendizado de máquina posteriormente usando a mídia original, a versão incorreta dos componentes de aprendizado de máquina pode ser instalada. Quando a barra inicial detecta uma incompatibilidade de versão, ele é desligado e cria um arquivo de despejo.

Para evitar esse problema, certifique-se de instalar os novos recursos no mesmo nível de patch como a instância do servidor.

**A maneira errada de atualização:**

1. Instale o SQL Server 2016 sem os serviços de R.
2. Atualize a atualização cumulativa do SQL Server 2016 2.
3. Instale o R Services (no banco de dados) usando a mídia do RTM.

**A maneira correta de atualização:**

1. Instale o SQL Server 2016 sem os serviços de R.
2. Atualize o SQL Server 2016 para o nível de patch desejado. Por exemplo, instale o Service Pack 1 e, em seguida, a atualização cumulativa 2.
3. Para adicionar o recurso no nível do patch correto, execute novamente a instalação do SP1 e CU2 e, em seguida, escolha o R Services (no banco de dados). 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>Barra inicial não será iniciado se notação 8ponto3 é necessária

> [!NOTE] 
> Em sistemas mais antigos, barra inicial pode falhar ao iniciar se há um requisito de notação 8ponto3. Esse requisito foi removido em versões posteriores. Clientes de serviços do SQL Server 2016 R devem instalar um dos seguintes:
> * SQL Server 2016 SP1 e CU1: [atualização cumulativa 1 para SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, a atualização cumulativa 3 e isso [hotfix](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), que está disponível sob demanda.

Para compatibilidade com R, SQL Server 2016 R Services (no banco de dados) necessária a unidade em que o recurso está instalado para dar suporte a criação de nomes de arquivos curtos usando *8ponto3 notação*. Também é chamado de um nome de 8.3 arquivo um *nome curto de arquivo*, e ele é usado para compatibilidade com versões anteriores do Microsoft Windows ou como uma alternativa para nomes de arquivo longos.

Se o volume em que você está instalando o R não oferece suporte a nomes de arquivos curtos, os processos que inicie R do SQL Server não podem ser capazes de localizar o executável correto e barra inicial não será iniciado.

Como alternativa, você pode habilitar a notação de 8ponto3 no volume em que o SQL Server está instalado e onde R Services está instalado. Em seguida, será necessário fornecer o nome curto para o diretório de trabalho no arquivo de configuração do R Services.

1. Para habilitar a notação 8ponto3, execute o utilitário fsutil com a *8dot3name* argumento conforme descrito aqui: [8dot3name fsutil](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Depois que a notação 8ponto3 estiver habilitada, abra o arquivo RLauncher.config e anote a propriedade de `WORKING_DIRECTORY`. Para obter informações sobre como encontrar esse arquivo, consulte [coleta de dados para a solução de problemas de aprendizado de máquina](data-collection-ml-troubleshooting-process.md).

3. Use o utilitário fsutil com a *arquivo* argumento para especificar um caminho de arquivo curto para a pasta especificada no WORKING_DIRECTORY.

4. Edite o arquivo de configuração para especificar a mesma pasta de trabalho que você inseriu na propriedade WORKING_DIRECTORY. Como alternativa, você pode especificar um diretório de trabalho diferentes e escolha um caminho existente que já é compatível com a notação de 8ponto3.


## <a name="next-steps"></a>Próximas etapas

[Problemas conhecidos e solução de problemas de serviços de aprendizado de máquina](machine-learning-troubleshooting-faq.md)

[Coleta de dados para solucionar problemas de aprendizado de máquina](data-collection-ml-troubleshooting-process.md)

[Perguntas frequentes sobre atualização e instalação](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Solucionar problemas de conexões do mecanismo de banco de dados](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
