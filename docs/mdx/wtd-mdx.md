---
title: WTD (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c572b517d82c5cd1d91492be8f9fe299000ec19c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582528"
---
# <a name="wtd-mdx"></a>Wtd (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna um conjunto de membros irmãos do mesmo nível como um determinado membro, começando com o primeiro irmão e terminando com um determinado membro, restringido pelo nível Semana na dimensão Tempo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Member_Expression*  
 Uma linguagem MDX válida que retorna um membro.  
  
## <a name="remarks"></a>Remarks  
 Se uma expressão de membro não for especificada, o padrão será o membro atual da primeira hierarquia com um nível de tipo semanas na primeira dimensão do tipo tempo (**Time.CurrentMember**) no grupo de medidas.  
  
 O **Wtd** é uma função de atalho para o [PeriodsToDate](../mdx/periodstodate-mdx.md) função em que o nível é definido como *semanas*. Ou seja, `Wtd(Member_Expression)` é equivalente a `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>Consulte também  
 [Qtd &#40;MDX&#41;](../mdx/qtd-mdx.md)   
 [MTD &#40;MDX&#41;](../mdx/mtd-mdx.md)   
 [Acumulado no ano &#40;MDX&#41;](../mdx/ytd-mdx.md)   
 [Referência de função MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
