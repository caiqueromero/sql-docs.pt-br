---
title: "Método (SQLServerPreparedStatement) setRef | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerPreparedStatement.setRef
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1a09bbf9-6f8f-4a21-85d2-2182111b5ce7
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c774be35214dba19e9ffabf797145630d41ee09
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="setref-method-sqlserverpreparedstatement"></a>Método (SQLServerPreparedStatement) setRef
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o parâmetro designado como o objeto de referência fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final void setRef(int i,  
                         java.sql.Ref x)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *Eu*  
  
 Um **int** que indica o número do parâmetro.  
  
 *x*  
  
 Um objeto de referência.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método setRef é especificado pelo método setRef na interface PreparedStatement.  
  
## <a name="see-also"></a>Consulte também  
 [Membros de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  