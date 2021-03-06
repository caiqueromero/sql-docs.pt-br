---
title: Função Intersect (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7acc509891dd1c975ad819bd904e840e369f0d4b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578518"
---
# <a name="intersect-mdx"></a>Função Intersect (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna a interseção de dois conjuntos de entrada, mantendo as duplicatas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Intersect(Set_Expression1 , Set_Expression2 [ , ALL ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression1*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
 *Set_Expression2*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
## <a name="remarks"></a>Remarks  
 O **Intersect** função retorna a interseção de dois conjuntos. Por padrão, a função remove as duplicações antes de interseccionar os dois conjuntos. Os dois conjuntos devem ter a mesma dimensionalidade.  
  
 Opcional **todos os** sinalizador preservará as duplicações. Se **todos os** for especificado, o **Intersect** função intercepta fará elementos como de costume e também interseccionará cada duplicação do primeiro conjunto que tem uma duplicação correspondente no segundo conjunto. Os dois conjuntos devem ter a mesma dimensionalidade.  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir retorna os anos de 2003 e 2004, os dois membros que aparecem em ambos os conjuntos especificados:  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001], [Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003]}`  
  
 `, {[Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 A consulta a seguir falha porque os dois conjuntos especificados contêm membros de hierarquias diferentes:  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001]}`  
  
 `, {[Customer].[City].&[Abingdon]&[ENG]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
