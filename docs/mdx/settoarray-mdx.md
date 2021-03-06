---
title: SetToArray (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2239249c7372c7132861fbcb74dbe5079a4ae4eb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580998"
---
# <a name="settoarray-mdx"></a>SetToArray (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Converte um ou mais conjuntos para uma matriz para uso em uma função definida pelo usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression1*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
 *Set_Expression2*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
 *Numeric_Expression*  
 Uma expressão numérica válida, geralmente uma linguagem MDX de coordenadas de célula, que retorna um número.  
  
## <a name="remarks"></a>Remarks  
 O **SetToArray** função converte um ou mais conjuntos em uma matriz para uso em uma função definida pelo usuário. O número de dimensões na matriz resultante é igual ao número de conjuntos especificados.  
  
 A expressão numérica opcional pode fornecer os valores nas células da matriz. Se uma expressão numérica não for especificada, a junção cruzada dos conjuntos será avaliada no contexto atual.  
  
 As coordenadas da célula na matriz resultante correspondem à posição dos conjuntos na lista. Por exemplo, há três conjuntos: `SA`, `SB` e `SC`. Cada um desses conjuntos tem dois elementos. A instrução MDX, `SetToArray(SA, SB, SC)`, cria a matriz tridimensional a seguir:  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  O tipo de retorno de **SetToArray** função é o tipo de VARIANTE, VT_ARRAY. Portanto, a saída de **SetToArray** função deve ser usada somente como entrada para uma função definida pelo usuário.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna uma matriz.  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
