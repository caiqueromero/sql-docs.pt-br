---
title: NonEmpty (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a718a7e75a9b31b7d35cdc33883c97739aee68c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580278"
---
# <a name="nonempty-mdx"></a>NonEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna o conjunto de tuplas que não estão vazias a partir de um conjunto especificado, com base no produto cruzado do conjunto especificado com um segundo conjunto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
NONEMPTY(set_expression1 [,set_expression2])  
```  
  
## <a name="arguments"></a>Argumentos  
 *set_expression1*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
 *set_expression2*  
 Uma expressão MDX (Multidimensional Expressions) válida que retorna um conjunto.  
  
## <a name="remarks"></a>Remarks  
 Essa função retorna as tuplas do primeiro conjunto especificado que não estão vazias, quando avaliadas pelas tuplas do segundo conjunto. O **NonEmpty** função leva em conta os cálculos e preserva as tuplas duplicadas. Se um segundo conjunto não for fornecido, a expressão será avaliada no contexto das coordenadas atuais dos membros das hierarquias de atributos e medidas no cubo.  
  
> [!NOTE]  
>  Use essa função em vez de preterido [NonEmptyCrossjoin &#40;MDX&#41; ](../mdx/nonemptycrossjoin-mdx.md) função.  
  
> [!IMPORTANT]  
>  Não vazia é uma característica das referências de células pelas tuplas, não as próprias tuplas.  
  
## <a name="examples"></a>Exemplos  
 A consulta a seguir mostra um exemplo simples de **NonEmpty**, retornando todos os clientes que tinham um valor não nulo para o volume de vendas pela Internet em 1º de julho de 2001:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 O exemplo a seguir retorna o conjunto de tuplas contendo clientes e datas de compra, usando o **filtro** função e o **NonEmpty** funções para localizar a última data em que uma compra feita pelo cliente:  
  
 `WITH SET MYROWS AS FILTER`  
  
 `(NONEMPTY`  
  
 `([Customer].[Customer Geography].[Customer].MEMBERS`  
  
 `* [Date].[Date].[Date].MEMBERS`  
  
 `, [Measures].[Internet Sales Amount]`  
  
 `) AS MYSET`  
  
 `, NOT(MYSET.CURRENT.ITEM(0)`  
  
 `IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))`  
  
 `)`  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `MYROWS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Consulte também  
 [DefaultMember &#40;MDX&#41;](../mdx/defaultmember-mdx.md)   
 [Filtro &#40;MDX&#41;](../mdx/filter-mdx.md)   
 [IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)   
 [Referência de função MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)  
  
  
