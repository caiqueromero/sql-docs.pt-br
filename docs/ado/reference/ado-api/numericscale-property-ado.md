---
title: Propriedade NumericScale (ADO) | Microsoft Docs
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
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 575618ad1760cdca6c32e1b8e2797070583506de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="numericscale-property-ado"></a>Propriedade NumericScale (ADO)
Indica a escala de valores numéricos em uma [parâmetro](../../../ado/reference/ado-api/parameter-object.md) ou [campo](../../../ado/reference/ado-api/field-object.md) objeto.  
  
## <a name="settings-and-return-values"></a>Configurações e valores de retorno  
 Define ou retorna um **bytes** valor que indica o número de casas decimais para os valores numéricos serão resolvido.  
  
## <a name="remarks"></a>Remarks  
 Use o **NumericScale** propriedade para determinar o número de dígitos à direita da vírgula decimal será usado para representar valores para um numérico **parâmetro** ou **campo** objeto.  
  
 Para **parâmetro** objetos, o **NumericScale** propriedade é leitura/gravação.  
  
 Para uma **campo**objeto, **NumericScale** é normalmente somente leitura. No entanto, para o novo **campo** objetos que foram acrescentados ao [campos](../../../ado/reference/ado-api/fields-collection-ado.md) coleção de um [registro](../../../ado/reference/ado-api/record-object-ado.md), **NumericScale** é leitura/gravação somente após o [valor](../../../ado/reference/ado-api/value-property-ado.md) propriedade para o **campo** foi especificado e o provedor de dados foi adicionado com êxito o novo **campo** chamando o [ Atualização](../../../ado/reference/ado-api/update-method.md) método o [campos](../../../ado/reference/ado-api/fields-collection-ado.md) coleção.  
  
## <a name="applies-to"></a>Aplica-se a  
  
|||  
|-|-|  
|[Objeto Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Objeto Field](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de propriedades de precisão (VB) e NumericScale](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Exemplo de propriedades de precisão (VC + +) e NumericScale](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Propriedade Precision (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
