---
title: Onde o elemento (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 119a702b28956c5570d30e3692b7d7339f49486f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580008"
---
# <a name="where-element-xmla"></a>Elemento Where (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Define uma condição de filtro usada pelo comando pai [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) ou [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<Drop> <!-- or Update -->  
   ...  
   <Where>  
      <Attributes>...</Attributes>  
   </Where>  
   ...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Nenhum|  
|Valor padrão|Nenhum|  
|Cardinalidade|1-1: elemento obrigatório que ocorre apenas uma única vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|[Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Elementos filho|[Atributos](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Para comandos **Drop**, o elemento **Where**, combinado com o elemento [DeleteWithDescendants](../../../analysis-services/xmla/xml-elements-properties/deletewithdescendants-element-xmla.md), identifica o escopo dos membros de atributo a serem descartados.  
  
 Para comandos **Update** , o elemento **Where** identifica o escopo dos membros de atributo a serem atualizados. Vários membros de atributo podem ser atualizados com uma combinação de atributos incluídos na coleção **Attributes** do comando pai **Update** e na coleção **Attributes** do elemento **Where** .  
  
 Para obter mais informações sobre a exclusão e atualização de membros de atributo, consulte [Inserindo, atualizando e descartando membros &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Confira também
 [Propriedades &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
