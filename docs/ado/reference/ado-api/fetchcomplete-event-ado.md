---
title: Evento FetchComplete (ADO) | Microsoft Docs
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
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59c3adb6b0ad683b40dac2cf4547800bf7398067
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="fetchcomplete-event-ado"></a>Evento FetchComplete (ADO)
O **FetchComplete** eventos é chamado depois que todos os registros em uma operação assíncrona demorada foram recuperados para o [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *pError*  
 Um [erro](../../../ado/reference/ado-api/error-object.md) objeto. Descreve o erro ocorrido se o valor de **adStatus** é **adStatusErrorsOccurred**; caso contrário, ele não está definido.  
  
 *adStatus*  
 Um [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valor de status. Quando esse evento é chamado, esse parâmetro é definido como **adStatusOK** se a operação que causou o evento foi bem-sucedida, ou para **adStatusErrorsOccurred** se a operação falhou.  
  
 Antes desse evento retorna, defina este parâmetro como **adStatusUnwantedEvent** para impedir que as notificações subsequentes.  
  
 *pRecordset*  
 Um **registros** objeto. O objeto para o qual os registros foram recuperados.  
  
## <a name="remarks"></a>Remarks  
 Para usar **FetchComplete** com o Microsoft Visual Basic, Visual Basic 6.0 ou posterior é necessário.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de modelo de eventos do ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Resumo do manipulador de eventos ADO](../../../ado/guide/data/ado-event-handler-summary.md)
