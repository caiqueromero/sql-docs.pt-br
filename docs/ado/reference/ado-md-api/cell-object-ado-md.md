---
title: Célula do objeto (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22227f22f42e5848b0826028a855b31b4b82443a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="cell-object-ado-md"></a>Objeto de célula (ADO MD)
Representa os dados na interseção de coordenadas de eixo contidos em um conjunto de células.  
  
## <a name="remarks"></a>Remarks  
 Um **célula** retornado pelo objeto de [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) propriedade de um [conjunto de células](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objeto.  
  
 Com as coleções e propriedades de um **célula** do objeto, você pode fazer o seguinte:  
  
-   Retornar os dados de **célula** com o [valor](../../../ado/reference/ado-md-api/value-property-ado-md.md) propriedade.  
  
-   Retorna a cadeia de caracteres que representa a exibição formatada do **valor** propriedade com o [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) propriedade.  
  
-   Retorna o valor ordinal do **célula** dentro de **conjunto de células** com o [Ordinal](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) propriedade.  
  
-   Determinar a posição do **célula** dentro de [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) com o [posições](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) coleção.  
  
-   Recuperar outras informações sobre o **célula** com ADO padrão [propriedades](../../../ado/reference/ado-api/properties-collection-ado.md) coleção.  
  
 O **propriedades** coleção contém propriedades fornecidos pelo provedor. A tabela a seguir lista as propriedades que podem estar disponíveis. A lista de propriedade real pode ser diferente dependendo da implementação do provedor. Consulte a documentação do provedor para obter uma lista mais completa de propriedades disponíveis.  
  
|Nome|Description|  
|----------|-----------------|  
|BackColor|Cor de plano de fundo usada ao exibir a célula.|  
|FontFlags|Bitmask que detalha os efeitos da fonte.|  
|FontName|Fonte usada para exibir o valor da célula.|  
|FontSize|Tamanho da fonte usado para exibir o valor da célula.|  
|ForeColor|Cor de primeiro plano usada ao exibir a célula.|  
|FormatString|Valor em uma cadeia de caracteres formatada.|  
  
 Esta seção contém o tópico a seguir.  
  
-   [Propriedades, métodos e eventos](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de eixo (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Objeto de conjunto de células (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Coleção de posições (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Coleção Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
