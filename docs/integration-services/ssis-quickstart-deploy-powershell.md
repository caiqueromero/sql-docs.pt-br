---
title: Implantar um projeto do SSIS com o PowerShell | Microsoft Docs
ms.date: 09/25/2017
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3f19d2fc8324f87c6792fa568cc736a7cd7aafec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="deploy-an-ssis-project-with-powershell"></a>Implantar um projeto do SSIS com o PowerShell
Este tutorial de início rápido demonstra como usar um script do PowerShell para se conectar a um servidor de banco de dados e implantar um projeto do SSIS no catálogo do SSIS.

## <a name="powershell-script"></a>Script do PowerShell
Forneça os valores adequados para as variáveis na parte superior do script a seguir e, em seguida, execute o script para implantar o projeto do SSIS.

> [!NOTE]
> O exemplo a seguir usa a Autenticação do Windows. Para usar a autenticação do SQL Server, substitua o argumento `Integrated Security=SSPI;` com `User ID=<user name>;Password=<password>;`.

```powershell
# Variables
$SSISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"
$TargetServerName = "localhost"
$TargetFolderName = "Project1Folder"
$ProjectFilePath = "C:\Projects\Integration Services Project1\Integration Services Project1\bin\Development\Integration Services Project1.ispac"
$ProjectName = "Integration Services Project1"

# Load the IntegrationServices assembly
$loadStatus = [System.Reflection.Assembly]::Load("Microsoft.SQLServer.Management.IntegrationServices, "+
    "Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91, processorArchitecture=MSIL")

# Create a connection to the server
$sqlConnectionString = `
    "Data Source=" + $TargetServerName + ";Initial Catalog=master;Integrated Security=SSPI;"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

# Create the Integration Services object
$integrationServices = New-Object $SSISNamespace".IntegrationServices" $sqlConnection

# Get the Integration Services catalog
$catalog = $integrationServices.Catalogs["SSISDB"]

# Create the target folder
$folder = New-Object $SSISNamespace".CatalogFolder" ($catalog, $TargetFolderName,
    "Folder description")
$folder.Create()

Write-Host "Deploying " $ProjectName " project ..."

# Read the project file and deploy it
[byte[]] $projectFile = [System.IO.File]::ReadAllBytes($ProjectFilePath)
$folder.DeployProject($ProjectName, $projectFile)

Write-Host "Done."
```

## <a name="next-steps"></a>Próximas etapas
- Considere outras maneiras de implantar um pacote.
    - [Implantar um pacote do SSIS com SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Implantar um pacote do SSIS com o Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Implantar um pacote do SSIS com o Transact-SQL (VS Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Implantar um pacote do SSIS por meio do prompt de comando](./ssis-quickstart-deploy-cmdline.md)
    - [Implantar um pacote do SSIS com o C#](./ssis-quickstart-deploy-dotnet.md) 
- Execute um pacote implantado. Para executar um pacote, você pode escolher uma entre várias ferramentas e linguagens. Para saber mais, veja os tópicos a seguir:
    - [Executar um pacote do SSIS com o SSMS](./ssis-quickstart-run-ssms.md)
    - [Executar um pacote do SSIS com o Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Executar um pacote do SSIS com o Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Executar um pacote do SSIS no prompt de comando](./ssis-quickstart-run-cmdline.md)
    - [Executar um pacote do SSIS com o PowerShell](ssis-quickstart-run-powershell.md)
    - [Executar um pacote do SSIS com o C#](./ssis-quickstart-run-dotnet.md) 
