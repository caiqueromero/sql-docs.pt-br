---
title: SQL Server Native Client | Microsoft Docs
ms.date: 04/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 2efcd738e4f5e1047f5d265ea063e90a7cdb8de8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

SNAC ou SQL Server Native Client, é um termo que tenha sido usado alternadamente para se referir a drivers ODBC e OLE DB para SQL Server. 

**Para obter mais informações e baixar os Drivers de ODBC ou SNAC, visite [SNAC de ciclo de vida explicado](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).**

Para obter mais informações sobre o Driver ODBC para SQL Server, consulte [Microsoft ODBC Driver for SQL Server no Windows](https://msdn.microsoft.com/library/jj730314(v=sql.110).aspx).  Consulte também, [apresentando os novos Drivers de ODBC da Microsoft para SQL Server](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/), e [ODBC Driver 13.1 para SQL Server lançadas](https://blogs.technet.microsoft.com/dataplatforminsider/2016/08/03/odbc-driver-13-1-for-sql-server-released/).  
  
 Obter informações sobre o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recursos Native Client lançados com [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], a última versão disponível do SQL Server native Client: 
  
-   [Suporte do SQL Server Native Client para LocalDB](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  
  
-   [Descoberta de metadados](../../relational-databases/native-client/features/metadata-discovery.md)  
  
-   [Suporte a UTF-16 no SQL Server Native Client 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [Suporte do SQL Server Native Client à alta disponibilidade e recuperação de desastre](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Acessar informações de diagnóstico nos logs de eventos estendidos](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
ODBC em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client oferece suporte a três recursos que foram adicionados ao ODBC padrão no SDK do Windows 7:  
  
-   Execução assíncrona em operações relacionadas à conexão. Para obter mais informações, consulte [Execução assíncrona](http://go.microsoft.com/fwlink/?LinkID=191493).  
  
-   Extensibilidade do tipo de dados C. Para obter mais informações, consulte [Tipos de dados C em ODBC](http://go.microsoft.com/fwlink/?LinkID=191495).  
  
     Para dar suporte a esse recurso no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, SQLGetDescField pode retornar **SQL_C_SS_TIME2** (para **tempo** tipos) ou **SQL_C_SS_TIMESTAMPOFFSET** (para **datetimeoffset**) em vez de **SQL_C_BINARY**, se seu aplicativo usar o ODBC 3.8. Para obter mais informações, consulte [suporte de tipo de dados para aprimoramentos de hora e data de ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  
  
-   Chamando **SQLGetData** várias vezes com um buffer pequeno para recuperar um valor de parâmetro grande. Para obter mais informações, consulte [Recuperando parâmetros de saída usando SQLGetData](http://go.microsoft.com/fwlink/?LinkID=191494).  
  
 Os tópicos a seguir descrevem as alterações de comportamento do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client no [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   Ao chamar **ICommandWithParameters::SetParameterInfo**, o valor transmitido ao parâmetro *pwszName* deve ser um identificador válido. Para obter mais informações, consulte [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  
  
-   **SQLDescribeParam** consistentemente retornará um valor de conformidade de especificação do ODBC. Para obter mais informações, consulte [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  
  
-   [Alteração de comportamento do driver ODBC ao lidar com conversões de caracteres](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a>Consulte também  
[Instale o SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [Recursos do SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  