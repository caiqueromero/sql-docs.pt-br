---
title: Interface ISQLServerStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f83b514-6e76-4f37-baf3-a10db2010e7c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c292f5540706e924ecf56b5e34174d041af1b21e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="isqlserverstatement-interface"></a>Interface ISQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Representa a implementação básica da funcionalidade de instrução JDBC. Essa interface foi adicionada ao [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0.  
  
 **Pacote:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** Java.SQL. Statement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public interface ISQLServerStatement  
```  
  
## <a name="remarks"></a>Remarks  
 Essa interface é implementada por [classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 Essa interface expõe os seguintes [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-métodos específicos:  
  
|Método|Para obter mais informações, consulte|  
|------------|-------------------------------|  
|public String getResponseBuffering|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|  
|public void setResponseBuffering|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Referência da API do Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
