---
title: Método modify() (tipo de dados xml) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|xml
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 01ad2afc24c09cdd6a05189335f1e0d6827d24c4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="modify-method-xml-data-type"></a>Método modifique() (Tipo de dados xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifica o conteúdo de um documento XML. Use esse método para modificar o conteúdo de uma coluna ou variável do tipo **xml**. Esse método utiliza uma instrução XML DML para inserir, atualizar ou excluir nós de dados XML. O método **modify()** do tipo de dados **xml** pode ser usado apenas na cláusula SET de uma instrução UPDATE.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>Argumentos  
 XML_DML  
 É uma cadeia de caracteres em XML DML (linguagem de manipulação de dados). O documento XML é atualizado de acordo com essa expressão.  
  
> [!NOTE]  
>  Um erro será retornado se o método **modify()** for chamado em um valor nulo ou resultar em valor nulo.  
  
## <a name="examples"></a>Exemplos  
 Como o método **modify()** exige uma cadeia de caracteres em XML DML (Linguagem de Manipulação de Dados), os exemplos para **modify()** estão contidos nos tópicos que descrevem as instruções XML DML. Para obter esses exemplos, consulte [insert &#40;XML DML&#41;](../../t-sql/xml/insert-xml-dml.md), [delete &#40;XML DML&#41;](../../t-sql/xml/delete-xml-dml.md) e [replace value of &#40;XML DML&#41;](../../t-sql/xml/replace-value-of-xml-dml.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Criar instâncias de dados XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [Métodos de tipos de dados xml](../../t-sql/xml/xml-data-type-methods.md)   
 [XML DML &#40;linguagem de manipulação de dados XML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
