---
title: "Função Intersect (MDX) | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INTERSECT
dev_langs:
- kbMDX
helpviewer_keywords:
- Intersect function
ms.assetid: 0de8fbb4-e2db-480c-86f1-2abbbcfdb1d8
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 07f59caff53819cb2ccea52d7f3372a4d3b97c65
ms.contentlocale: pt-br
ms.lasthandoff: 08/02/2017

---
# <a name="intersect-mdx"></a>Função Intersect (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Comentários  
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
 [Referência de função MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
