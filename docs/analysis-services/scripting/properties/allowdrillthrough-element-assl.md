---
title: Elemento AllowDrillThrough (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 25bad363975494fc8bd6c8cb343a165d8bb85f85
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="allowdrillthrough-element-assl"></a>Elemento AllowDrillThrough (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Determina se a extração de detalhes é permitida no elemento pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Boolean|  
|Valor padrão|**Falso**|  
|Cardinalidade|0-1: Elemento opcional que pode ocorrer uma vez, e somente uma vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|[Elemento MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
|Elementos filho|Nenhuma|  
  
## <a name="remarks"></a>Remarks  
 Os elementos que correspondem aos pais de **AllowDrillThrough** no modelo de objeto de Analysis Management Objects (AMO) são <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, e <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Detalhamento em estruturas de mineração  
 Em [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], você pode definir **AllowDrillthrough** permissões para estruturas de mineração, bem como modelos de mineração. Quando você atribuir permissões a uma função, qualquer membro dessa função poderá consultar o modelo de mineração de dados e retornar as colunas de estrutura que não foram incluídas no modelo. Por exemplo, você cria um modelo que usa apenas estas colunas: chave do cliente, renda do cliente e compras do cliente. Ao ativar o detalhamento no modelo, os usuários podem retornar informações de outras colunas da estrutura de mineração, como emails ou nomes de cliente.  
  
 Portanto, para proteger dados confidenciais, tenha cuidado quando for adicionar colunas à estrutura de mineração. Além disso, só conceda a permissão **AllowDrillthrough** em uma estrutura quando ele for necessária.  
  
 Para detalhar colunas de estrutura, use uma consulta com um dos seguintes formulários:  
  
 `SELECT * FROM <structure>.CASES`  
  
 ou  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>Consulte também  
 [Elemento Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Propriedades & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
