---
title: OPENROWSET (DMX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- OPENROWSET
dev_langs:
- DMX
helpviewer_keywords:
- OPENROWSET statement
ms.assetid: 8c8b61b4-2bf6-46c7-8976-51484004dc22
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f7ed5b65bf1f8ecf01d6b01939311de562eb85b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;consulta de fonte de dados&gt; -OPENROWSET
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Substitui uma consulta de dados de origem por uma consulta a um provedor externo. As instruções INSERT, SELECT FROM PREDICTION JOIN e SELECT FROM NATURAL PREDICTION JOIN oferecem suporte a **OPENROWSET**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
OPENROWSET(provider_name,provider_string,query_syntax)  
```  
  
## <a name="arguments"></a>Argumentos  
 *provider_name*  
 Nome de um provedor de OLE DB.  
  
 *provider_string*  
 Cadeia de conexão OLE DB para o provedor especificado.  
  
 *query_syntax*  
 Sintaxe de consulta que retorna um conjunto de linhas.  
  
## <a name="remarks"></a>Remarks  
 O provedor de mineração de dados estabelecerá uma conexão com o objeto de fonte de dados usando *provider_name* e *provider_string,* e executará a consulta especificada no *query_syntax* para recuperar o conjunto de linhas de dados de origem.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir pode ser usado em uma instrução PREDICTION JOIN para recuperar dados do banco de dados [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], usando uma instrução [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT.  
  
```  
OPENROWSET  
(  
'SQLOLEDB.1',  
'Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security     Info=False;Initial Catalog=AdventureWorksDW2012;Data Source=localhost',  
'SELECT TOP 1000 * FROM vTargetMail'  
)  
```  
  
## <a name="see-also"></a>Consulte também  
 [&#60;consulta de fonte de dados&#62;](../dmx/source-data-query.md)   
 [Extensões de mineração de dados &#40;DMX&#41; instruções de manipulação de dados](../dmx/dmx-statements-data-manipulation.md)   
 [Extensões de mineração de dados & #40; DMX & #41; Referência de instrução](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
