---
title: Barras duplas (comentário) (DMX) | Microsoft Docs
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
dev_langs:
- DMX
helpviewer_keywords:
- double forward slashes
- commenting characters
- // (comment)
ms.assetid: c2ab9ca1-9fc9-4162-97f9-a9433d189220
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 72d91543e9e384f48f4e1220e5926fedbb5787f4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="double-slash-comment-dmx"></a>Barras duplas (comentário) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica uma cadeia de caracteres de texto que o [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] não deve executar. É possível aninhar comentários em uma instrução DMX (Data Mining Extensions), incluí-los no final de uma linha de código ou inseri-los em uma linha separada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>Parâmetros  
 *Comment_Text*  
 Cadeia de caracteres que contém o texto do comentário.  
  
## <a name="remarks"></a>Remarks  
 Use // somente para comentários de linha única. Os comentários inseridos com o uso de // são delimitados pelo caractere de nova linha.  
  
 Não há comprimento máximo para comentários.  
  
 Para obter mais informações sobre como usar tipos diferentes de comentários em DMX, consulte [comentários &#40;DMX&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estrela de barra &#40;comentário&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)   
 [– &#40;Comentário&#41; &#40;DMX&#41; resumo](../dmx/comment-dmx-summary.md)   
 [Extensões de mineração de dados &#40;DMX&#41; referência de operador](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operadores &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
