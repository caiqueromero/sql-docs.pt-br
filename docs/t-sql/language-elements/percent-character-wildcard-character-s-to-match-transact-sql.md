---
title: Caractere de porcentagem (curinga – caracteres a serem correspondidos) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Data Warehouse
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- '%'
- '%_TSQL'
- wildcard
dev_langs:
- TSQL
helpviewer_keywords:
- conditions [SQL Server], wildcards
- '% (wildcard - character(s) to match)'
- matching conditions [SQL Server]
- wildcard characters [SQL Server]
- characters [SQL Server], wildcard
ms.assetid: d4cbc1a9-37e1-4101-97fb-e6ac30c1223e
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d656c7508d82f958b5a2be2d772c065f14cac6c1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="percent-character-wildcard---characters-to-match-transact-sql"></a>Caractere de porcentagem (Curinga - Caracteres de Correspondência) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Corresponde a qualquer cadeia de zero ou mais caracteres. Esse caractere curinga pode ser usado como um prefixo ou como um sufixo.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna todos os nomes das pessoas na tabela `Person` do `AdventureWorks2012` que começam com `Dan`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Dan%';  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Operadores &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Expressões &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
 [&#91; &#93; (curinga – caracteres a serem correspondidos)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
  [&#91;^&#93; (Curinga – caracteres para não correspondência)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [_ (Curinga – Corresponder um caractere)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  
