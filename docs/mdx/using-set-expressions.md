---
title: Usando o conjunto de expressões | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b384bffc84140b966ea510834054c65986ba292
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581718"
---
# <a name="using-set-expressions"></a>Usando expressões de conjunto
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Um conjunto é composto por uma lista ordenada de nenhuma ou algumas tuplas. Um conjunto que não contém nenhuma tupla é conhecido como um conjunto vazio.  
  
 A expressão completa de um conjunto consiste em nenhuma ou algumas tuplas especificadas explicitamente, entre chaves:  
  
 {[{ *Tuple_expression* | *Member_expression* } [, { *Tuple_expression* | *Member_expression* }]...]}  
  
 As expressões de membro especificadas em uma expressão de conjunto são convertidas em expressões de tupla de um membro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra duas expressões de conjunto usadas nos eixos Colunas e Linhas de uma consulta:  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 No eixo Colunas, o conjunto  
  
 {[Medidas].[Valor das Vendas pela Internet], [Medidas].[Valor do Imposto da Internet]}  
  
 consiste em dois membros da dimensão Medidas. No eixo Linhas, o conjunto  
  
 {([Produto].[Categorias de Produto].[Categoria].&[4], [Data].[Calendário].[Ano Civil].&[2004]),  
  
 ([Produto].[Categorias de Produto].[Categoria].&[1], [Data].[Calendário].[Ano Civil].&[2003]),  
  
 ([Produto].[Categorias de Produto].[Categoria].&[3], [Data].[Calendário].[Ano Civil].&[2004])}  
  
 consiste em três tuplas, cada uma contendo duas referências explícitas aos membros da hierarquia Categorias de Produto da dimensão Produto e da hierarquia Calendário da dimensão Data.  
  
 Para obter exemplos de funções que retornam conjuntos, consulte [trabalhando com membros, tuplas e conjuntos de &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Consulte também  
 [Expressões &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
