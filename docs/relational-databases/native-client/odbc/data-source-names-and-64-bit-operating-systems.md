---
title: Nomes e sistemas operacionais de 64 bits da fonte de dados | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6ee9d8d8feff705ee303098a829573bb470b3607
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Nomes de fonte de dados e sistemas operacionais de 64 bits
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Para compilar e executar um aplicativo como sendo de 32 bits em um sistema operacional de 64 bits, você precisa criar a fonte de dados ODBC com o Administrador ODBC em %windir%\SysWOW64\odbcad32.exe.  
  
## <a name="remarks"></a>Remarks  
 Um sistema operacional Windows de 64 bits tem dois arquivos odbcad32.exe:  
  
-   %SystemRoot%\system32\odbcad32.exe é usado criar e manter nomes da fonte de dados para aplicativos de 64 bits.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe é usado criar e manter nomes da fonte de dados para aplicativos de 32 bits, incluindo aplicativos de 32 bits que são executados em sistemas operacionais de 64 bits.  
  
## <a name="see-also"></a>Consulte também  
 [Cliente nativo do SQL Server & #40; ODBC & #41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
