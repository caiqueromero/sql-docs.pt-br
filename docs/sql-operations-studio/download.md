---
title: Baixe e instale o Studio de operações do Microsoft SQL (visualização) | Microsoft Docs
description: Baixar e instalar o Microsoft SQL operações Studio (visualização) para Windows, macOS ou Linux
ms.custom: tools|sos
ms.date: 05/08/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dcf6f9d14efd903c47d4e3b059503fb77606209b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Baixe e instale o Studio de operações do SQL (visualização)

[!INCLUDE[name-sos](../includes/name-sos.md)] executa no Linux, Windows e macOS.

Baixe e instale a versão mais recente, o *visualização pública pode*:

|Plataforma|Download|Data de lançamento| Versão |
|:---|:---|:---|:---|
|Windows|[Instalador](https://go.microsoft.com/fwlink/?linkid=873386)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=873387)|7 de maio de 2018 |0.29.3|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=873388)|7 de maio de 2018 |0.29.3|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=873391)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=873390)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=873389)|7 de maio de 2018 |0.29.3|

Para obter detalhes sobre a versão mais recente, consulte o [notas de versão](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Obter o Studio de operações do SQL (visualização) para Windows

Esta versão do [!INCLUDE[name-sos](../includes/name-sos-short.md)] inclui uma experiência de instalação padrão do Windows e. zip: 

**Instalador**

1. Baixe e execute o [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] installer para Windows](https://go.microsoft.com/fwlink/?linkid=873386).
1. Iniciar o [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] aplicativo.


**arquivo. zip**

1. Baixar [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] . zip para o Windows](https://go.microsoft.com/fwlink/?linkid=873387).
2. Navegue até o arquivo baixado e extraia-o.
3. Execute `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Obter o Studio de operações do SQL (visualização) para macOS

1. Baixar [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] para macOS](https://go.microsoft.com/fwlink/?linkid=873388).
2. Para expandir o conteúdo do zip, clique duas vezes nele.
3. Para fazer [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponíveis no *Launchpad*, arraste *sqlops.app* para o *aplicativos* pasta.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Obter o Studio de operações do SQL (visualização) para Linux

1. Baixar [!INCLUDE[name-sos](../includes/name-sos-short.md)] para Linux usando um dos instaladores ou o arquivamento gz:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=873391)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=873390)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=873389)
1. Para extrair o arquivo e inicialização [!INCLUDE[name-sos](../includes/name-sos-short.md)], abra uma nova janela do Terminal e digite os seguintes comandos:

   **Instalação Debian:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   **rpm instalação:**
   ```bash
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
   ```

   **gz instalação:**
   ```bash 
   cd ~ 
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~ 
   tar -xvf ~/sqlops-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   sqlops 
   ``` 

   > [!NOTE]
   > No Debian, Redhat e Ubuntu, você pode ter dependências ausentes. Use os comandos a seguir para instalar essas dependências, dependendo de sua versão do Linux:
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **RedHat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-sql-operations-studio-preview"></a>Desinstalar o Studio de operações do SQL (visualização)

Se você instalou [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] usando o Windows installer, desinstale da mesma maneira que você remova qualquer aplicativo do Windows.

Se você instalou [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] . zip ou outro arquivo, em seguida, simplesmente excluir os arquivos.

## <a name="supported-operating-systems"></a>Sistemas operacionais com suporte

[!INCLUDE[name-sos](../includes/name-sos-short.md)] executa no Linux, Windows e macOS e é suportado nas seguintes plataformas:

### <a name="windows"></a>Windows
- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Requer o Windows 7 (SP1) (64 bits) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

### <a name="macos"></a>macOS
- macOS 10.13 Serra alta
- macOS 10.12 Serra

### <a name="linux"></a>Linux
- 7.4 do Red Hat Enterprise Linux
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Verificar atualizações
Para verificar as atualizações mais recentes, clique no ícone de engrenagem na parte inferior esquerda da janela e clique **verificar se há atualizações**

## <a name="next-steps"></a>Próximas etapas

Consulte um dos seguintes guias de início rápido para começar:
- [Conectar e consultar o SQL Server](quickstart-sql-server.md)
- [Conectar e consultar o banco de dados SQL do Azure](quickstart-sql-database.md)
- [Conectar e consultar o depósito de dados do Azure](quickstart-sql-dw.md)

Contribuir com [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Declaração de privacidade do Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) e [coleta de dados de uso](usage-data-collection.md).
