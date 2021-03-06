---
title: Requisitos do sistema, instalação e arquivos de Driver | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10e4d020bac05317e76dabea46495d58def71cf0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="system-requirements-installation-and-driver-files"></a>Requisitos do sistema, instalação e arquivos de driver
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

O ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] dá suporte a conexões para SQL Server 2014, SQL Server 2012 R2, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro_md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]e [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)].  
  
O ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] no Windows pode ser instalado em um computador que também tenha uma ou mais versões do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client.  
  
O ODBC Driver 13 e 13.1 para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], além do citado acima, dá suporte ao SQL Server 2016. 

17 de Driver de ODBC para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] oferece suporte a todos os acima e também 2017 do SQL Server.
  
O nome do driver que você especificar em uma cadeia de caracteres de conexão é `ODBC Driver 11 for SQL Server` ou `ODBC Driver 13 for SQL Server` (para 13 e 13.1) ou `ODBC Driver 17 for SQL Server`.
  
## <a name="supported-operating-systems"></a>Sistemas operacionais com suporte

Você pode executar aplicativos com o driver nos seguintes sistemas operacionais Windows:  

-   Windows Server 2008 R2 
-   Windows Server 2012
-   Windows Server 2012 R2    
-   Windows Vista SP2 *(somente do ODBC Driver 11)*  
-   Windows 7  
-   Windows 8
-   Windows 8.1
-   Windows 10
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Instalando o Microsoft ODBC Driver para SQL Server

O driver é instalado quando você executa `msodbcsql.msi` de um dos links a seguir:

- [Baixar o Microsoft ODBC Driver 17 para SQL Server no Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Baixar o Microsoft ODBC Driver 13.1 para SQL Server no Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Baixar o Microsoft ODBC Driver 13 for SQL Server no Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Baixe o Microsoft ODBC Driver 11 para SQL Server no Windows](https://www.microsoft.com/download/details.aspx?id=36434). 

Ele pode ser instalada lado a lado com [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client.  

Quando você invoca `msodbcsql.msi`, somente os componentes de cliente são instalados por padrão. Os componentes de cliente são arquivos que oferecem suporte à execução de um aplicativo que foi desenvolvido usando o driver. Para instalar os componentes do SDK, especifique `ADDLOCAL=ALL` na linha de comando. Por exemplo:  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 Especifique `IACCEPTMSODBCSQLLICENSETERMS=YES` para aceitar os termos de licença do usuário final, se você usar o `/passive`, `/qn`, `/qb`, ou `/qr` opção para instalar. Essa opção deve ser especificada com todas as letras maiúsculas. Por exemplo:  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 Para fazer uma desinstalação silenciosa:  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
Quando um aplicativo usa o driver, o aplicativo deve indicar que depende do driver por meio da opção de instalação `APPGUID`. Isso permite que o instalador do driver informe os aplicativos dependentes antes de desinstalar. Para especificar uma dependência no driver, defina o `APPGUID` parâmetro de linha de comando ao seu código de produto na instalação silenciosa do driver. (É preciso criar um código de produto ao usar o Microsoft Installer para agrupar o programa de instalação do aplicativo.) Por exemplo:  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Ferramentas de linha de comando: sqlcmd.exe e bcp.exe

O `bcp.exe` e `sqlcmd.exe` ferramentas para uso com o driver pode ser baixado em [11 de utilitários de linha de comando do Microsoft SQL Server](http://www.microsoft.com/download/details.aspx?id=36433), [13 de utilitários de linha de comando do Microsoft para SQL Server](https://www.microsoft.com/download/details.aspx?id=52680), ou [Utilitários de linha de comando do Microsoft 13.1 para SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). O driver é um pré-requisito para instalar `sqlcmd.exe` e `bcp.exe`.
  
`bcp.exe` e `sqlcmd.exe` são instalados no `110\Tools` subpasta de `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` para a versão 11, e `130\Tools` para 13 e 13.1.

Um aplicativo que usa funções BCP deve especificar o driver da mesma versão fornecido com o arquivo de cabeçalho e biblioteca usada para compilar o aplicativo.  

Por exemplo, quando você compila um aplicativo ODBC com `msodbcsql11.lib` e `msodbcsql.h`, use "DRIVER = {ODBC Driver 11 para SQL Server}" na cadeia de conexão.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Componentes do Microsoft ODBC Driver para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] no Windows 
 O driver ODBC no Windows contém os seguintes componentes:
 
|Componente|Description|  
|---------------|-----------------|  
|msodbcsql17.dll ou <br> o msodbcsql13.dll ou <br> msodbcsql11.dll|O arquivo de biblioteca de vínculo dinâmico (DLL) que contém toda a funcionalidade do driver. Esse arquivo é instalado em % systemroot%\System32.|  
|msodbcdiag17.dll ou <br> msodbcdiag13.dll ou <br> msodbcdiag11.dll|O arquivo de biblioteca de vínculo dinâmico (DLL) que contém a interface de diagnóstico (rastreamento) do driver. Esse arquivo é instalado em % systemroot%\System32.|
|msodbcsqlr17.rll ou <br> o msodbcsqlr13.rll ou <br> msodbcsqlr11.rll|O arquivo de recursos que acompanha a biblioteca do driver. Esse arquivo é instalado em % SYSTEMROOT%\System32\1033.| 
|o s13ch_msodbcsql.chm ou <br> s11ch_msodbcsql.chm |O arquivo de Ajuda do Assistente de fonte de dados que documenta como criar uma fonte de dados para o driver. Esse arquivo é instalado em %SYSTEMROOT%\System32\1033 <br /> <br /> **Observação:** nenhum arquivo chm para 17 de Driver ODBC. |  
|msodbcsql.h|O arquivo de cabeçalho que contém todas as novas definições necessárias para usar o driver.<br /><br /> **Observação:**  você não pode referenciar msodbcsql.h e odbcss.h no mesmo programa.<br /><br /> h para 17 de Driver de ODBC ou 13 é instalado em %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> h para ODBC Driver 11 é instalado em %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib or <br> msodbcsql13.lib or <br> msodbcsql11.lib|O arquivo de biblioteca necessário para chamar o **bcp** funções de utilitário que fazem parte do driver.<br /><br /> **Observação:** se você fizer referência a este arquivo de biblioteca em seu programa, certifique-se de que está no caminho do sistema e no caminho do sistema dos que usam o aplicativo.<br /><br /> msodbcsql17.lib ou ao msodbcsql13.lib é instalado em %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> O msodbcsql11.lib é instalado em %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|

  
## <a name="see-also"></a>Consulte também  
 [Microsoft ODBC Driver for SQL Server no Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
