---
title: PredictAdjustedProbability (DMX) | Microsoft Docs
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
- PredictAdjustedProbability
dev_langs:
- DMX
helpviewer_keywords:
- PredictAdjustedProbability function
ms.assetid: 9a1e2ec5-5a37-4df6-a78e-26a495cc9301
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: aa419df2af3d18724437a9e7822e98f2b971a726
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="predictadjustedprobability-dmx"></a>PredictAdjustedProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna a probabilidade ajustada de um estado especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
PredictAdjustedProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Aplica-se a  
 Uma coluna escalar.  
  
## <a name="return-type"></a>Tipo de retorno  
 Valor escalar.  
  
## <a name="remarks"></a>Remarks  
 Se o estado previsto for omitido, o estado que tiver a mais alta probabilidade previsível será usado, excluindo-se a partição de estados faltantes. Para incluir a partição de estados faltantes, defina o \<estado previsto > para **INCLUDE_NULL**.  
  
 Para retornar a probabilidade ajustada para os estados faltantes, defina o \<estado previsto > como NULL.  
  
 O **PredictAdjustedProbability** função é um [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] extensão para o [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB para mineração de dados.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir usa uma junção de previsão natural para determinar se um indivíduo é provavelmente um comprador de bicicletas, com base no modelo de mineração da Árvore de decisão TM, e determina também a probabilidade ajustada para a previsão.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictAdjustedProbability([Bike Buyer]) AS [Adjusted Probability]  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Consulte também  
 [Extensões de mineração de dados &#40;DMX&#41; referência de função](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funções &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funções de previsão geral &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
