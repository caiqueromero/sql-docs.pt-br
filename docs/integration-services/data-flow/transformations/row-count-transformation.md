---
title: Transformação Contagem de Linhas | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0148a0b0844f0977ea89686692ae6a23ecc090e1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="row-count-transformation"></a>Transformação Contagem de Linhas
  A transformação Contagem de Linhas conta as linhas quando passam por um fluxo de dados e armazena a contagem final em uma variável.  
  
 Um pacote do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] pode usar contagens de linhas para atualizar as variáveis usadas em scripts, expressões e expressões de propriedade. Por exemplo, a variável que armazena a contagem de linhas pode atualizar o texto de mensagem em uma mensagem de email para incluir o número de linhas. A variável que a transformação Contagem de Linhas usa já deve existir e deve estar no escopo da tarefa de Fluxo de Dados ao qual esse fluxo com a transformação Contagem de Linhas pertence.  
  
 A transformação só armazena o valor da contagem de linhas na variável após a última linha ter passado pela transformação. Portanto, o valor da variável não é atualizado a tempo de usar o valor atualizado no fluxo de dados que contém a transformação Contagem de Linhas. Você pode usar a variável atualizada em um fluxo de dados separado.  
  
 Essa transformação tem uma entrada e uma saída. Não dá suporte a uma saída de erro.  
  
## <a name="configuration-of-the-row-count-transformation"></a>Configuração da transformação Contagem de Linhas  
 Você pode definir propriedades pelo Designer do [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou programaticamente.  
  
 A caixa de diálogo **Editor Avançado** reflete as propriedades que podem ser definidas programaticamente. Para obter mais informações sobre as propriedades que podem ser definidas na caixa de diálogo **Editor Avançado** ou programaticamente, clique em um dos seguintes tópicos:  
  
-   [Propriedades comuns](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriedades personalizadas da transformação](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Para obter informações sobre como definir as propriedades desse componente, consulte [Definir as propriedades de um componente de fluxo de dados](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Variáveis do SSIS &#40;Integration Services&#41;](../../../integration-services/integration-services-ssis-variables.md)   
 [Fluxo de Dados](../../../integration-services/data-flow/data-flow.md)   
 [Transformações do Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
