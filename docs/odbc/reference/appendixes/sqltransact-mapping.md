---
title: Mapeamento de SQLTransact | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e938a4eb7c605d1ed9cf71c038bcc7187e1a8cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqltransact-mapping"></a>Mapeamento de SQLTransact
**SQLTransact** é agora substituído pelo **SQLEndTran**. A principal diferença entre as duas funções é que **SQLEndTran** contém um argumento *HandleType*, que especifica o escopo do trabalho a ser feito. O *HandleType* argumento pode especificar o ambiente ou o identificador de conexão. A seguinte chamada para **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 é mapeado para  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Se *identificador da conexão* não é igual a SQL_NULL_HDBC. O *identificador da conexão* argumento é definido como o valor de *hdbc*.  
  
 **SQL_Transact** é mapeado para  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Se *identificador da conexão* é igual a SQL_NULL_HDBC. O *EnvironmentHandle* argumento é definido como o valor de *henv*.  
  
 Em ambos os casos anteriores, o *CompletionType* argumento é definido como o mesmo valor como *fType*.
