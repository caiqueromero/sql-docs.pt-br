---
title: TopSum (MDX) | Microsoft Docs
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
- TOPSUM
dev_langs:
- kbMDX
helpviewer_keywords:
- TopSum function
ms.assetid: e32496fd-4897-43c9-a388-4028609f4ffb
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 58a7bffc672af75c52eacca28f2e83d36a56af0c
ms.contentlocale: pt-br
ms.lasthandoff: 08/02/2017

---
# <a name="topsum-mdx"></a>TopSum (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Classifica um conjunto e retorna os elementos de nível mais alto cujo total cumulativo é pelo menos um valor especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
 *Value*  
 Uma expressão numérica válida que especifica o valor contra o qual cada tupla é comparada.  
  
 *Numeric_Expression*  
 Uma expressão numérica válida que geralmente é uma linguagem MDX que retorna uma medida.  
  
## <a name="remarks"></a>Comentários  
 O **TopSum** função calcula a soma de uma medida especificada avaliada em um conjunto especificado, classificando o conjunto em ordem decrescente. Em seguida, a função retorna os elementos com os valores mais altos, cujo total da expressão numérica especificada seja, pelo menos, o valor especificado. Essa função retorna o subconjunto menor de um conjunto cujo total cumulativo é pelo menos o valor especificado. Os elementos retornados são classificados do maior para menor.  
  
> [!IMPORTANT]  
>  Como o [BottomSum](../mdx/bottomsum-mdx.md) função, o **TopSum** função sempre quebra a hierarquia.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna, para a categoria Bicicleta, o menor conjunto de membros do nível Cidade na hierarquia Geografia, na dimensão Geografia, cujo total cumulativo que usa a medida Valor das Vendas do Revendedor é pelo menos a soma de 6.000.000 (começando com os membros desse conjunto com o maior número de vendas).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
