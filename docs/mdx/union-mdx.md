---
title: Union (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7712e1f925aa514ec059a88d46db05d337f0c140
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582228"
---
# <a name="union--mdx"></a>Union (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna um conjunto gerado pela união de dois conjuntos, retendo membros duplicados opcionalmente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Standard syntax  
Union(Set_Expression1, Set_Expression2 [,...n][, ALL])  
  
Alternate syntax 1  
Set_Expression1 + Set_Expression2 [+...n]  
  
Alternate syntax 2  
{Set_Expression1 , Set_Expression2 [,...n]}  
```  
  
## <a name="arguments"></a>Argumentos  
 *Expressão de conjunto 1*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
 *Expressão de conjunto 2*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
## <a name="remarks"></a>Remarks  
 Esta função retorna a união de dois ou mais conjuntos especificados *.* Com a sintaxe padrão e com a sintaxe alternativa 1, as duplicatas são eliminadas por padrão. Com a sintaxe padrão, usando o **todos os** sinalizador mantém as duplicatas no conjunto Unido. As duplicatas são excluídas do final do conjunto. Com a sintaxe alternativa 2, as duplicatas são sempre retidas.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos a seguir demonstram o comportamento do **união** usando cada sintaxe de função.  
  
### <a name="standard-syntax-duplicates-eliminated"></a>Sintaxe padrão, duplicatas eliminadas  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="standard-syntax-duplicates-retained"></a>Sintaxe padrão, duplicatas retidas  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   , ALL  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-1-duplicates-eliminated"></a>Sintaxe alternativa 1, duplicatas eliminadas  
  
```  
SELECT   
   [Date].[Calendar Year].children   
   + {[Date].[Calendar Year].[CY 2002]}   
   + {[Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-2-duplicates-retained"></a>Sintaxe alternativa 2, duplicatas retidas  
  
```  
SELECT   
   {[Date].[Calendar Year].children  
   , [Date].[Calendar Year].[CY 2002]  
   , [Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [+ &#40;União&#41; &#40;MDX&#41;](../mdx/union-mdx-operator-reference.md)   
 [Referência de função MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
