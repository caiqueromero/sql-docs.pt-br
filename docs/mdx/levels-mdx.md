---
title: Níveis (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2fba58261bb0ba8f91e8127b1d33b847accf0dc7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579508"
---
# <a name="levels-mdx"></a>Função Levels (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna o nível cuja posição em uma dimensão ou hierarquia é especificada por uma expressão numérica ou cujo nome é especificado por uma expressão de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Expressão_Hierarquia*  
 Uma linguagem MDX válida que retorna uma hierarquia.  
  
 *Level_Number*  
 Uma expressão numérica válida que especifica um número de nível.  
  
 *Level_Name*  
 Uma expressão de cadeia de caracteres válida que especifica um nome de nível.  
  
## <a name="remarks"></a>Remarks  
 Se um número de nível for especificado, o **níveis** função retorna o nível associado à posição de base zero especificada.  
  
 Se um nome de nível for especificado, o **níveis** função retorna o nível especificado.  
  
> [!NOTE]  
>  Use a sintaxe de expressão de cadeia de caracteres para funções definidas pelo usuário.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos a seguir ilustram cada o **níveis** sintaxes de função.  
  
### <a name="numeric"></a>Numérico  
 O exemplo a seguir retorna o nível País:  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>Cadeia de caracteres  
 O exemplo a seguir retorna o nível País:  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
