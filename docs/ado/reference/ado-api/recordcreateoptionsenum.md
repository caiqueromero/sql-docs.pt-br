---
title: RecordCreateOptionsEnum | Microsoft Docs
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
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3109e7e7116fac22e007c65167bb718edf2b29b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Especifica se um existente **registro** deve ser aberta ou um novo **registro** criado para o [registro](../../../ado/reference/ado-api/record-object-ado.md) objeto [abrir](../../../ado/reference/ado-api/open-method-ado-record.md) método. Os valores podem ser combinados com um operador AND.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|Cria um novo **registro** no nó especificado por *fonte* parâmetro, em vez de abrir um existente **registro**. Se os pontos de origem para um nó existente, em seguida, ocorre um erro de tempo de execução, a menos que **adCreateCollection** é combinado com **adOpenIfExists** ou **adCreateOverwrite**.|  
|**adCreateNonCollection**|0|Cria um novo **registro** do tipo [adSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adCreateOverwrite**|0x4000000|Modifica os sinalizadores de criação **adCreateCollection**, **adCreateNonCollection**, e **adCreateStructDoc**. Quando ou é usado com esse valor e um dos valores de sinalizador de criação, se a URL de origem aponta para um nó existente ou **registro**, em seguida, existente **registro** é substituído e um novo é criado em seu lugar. Esse valor não pode ser usado junto com **adOpenIfExists**.|  
|**adCreateStructDoc**|0x80000000|Cria um novo **registro** do tipo [adStructDoc](../../../ado/reference/ado-api/recordtypeenum.md), em vez de abrir um existente **registro**.|  
|**adFailIfNotExists**|-1|Padrão. Resulta em um erro de tempo de execução se *fonte* aponta para um nó inexistente.|  
|**adOpenIfExists**|0x2000000|Modifica os sinalizadores de criação **adCreateCollection**, **adCreateNonCollection**, e **adCreateStructDoc**. Quando ou é usado com esse valor e um dos valores de sinalizador de criação, se a URL de origem aponta para um nó existente ou **registro** do objeto, em seguida, o provedor deve abrir o **registro** em vez de criar um novo um. Esse valor não pode ser usado junto com **adCreateOverwrite**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Constantes não têm equivalentes do ADO/WFC.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Método Open (Registro do ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
