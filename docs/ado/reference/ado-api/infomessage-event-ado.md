---
title: Evento do InfoMessage (ADO) | Microsoft Docs
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7f1e479b4dfb5b9cb557030e03afeac3f6278720
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="infomessage-event-ado"></a>Evento do InfoMessage (ADO)
O **InfoMessage** evento é chamado sempre que ocorrer um aviso durante uma **ConnectionEvent** operação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *pError*  
 Um [erro](../../../ado/reference/ado-api/error-object.md) objeto. Este parâmetro contém erros que são retornados. Se vários erros são retornados, enumerar o **erros** coleção encontrá-las.  
  
 *adStatus*  
 Um [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valor de status. Se ocorrer um aviso, *adStatus* é definido como **adStatusOK** e *pError* contém o aviso.  
  
 Antes desse evento retorna, defina este parâmetro como **adStatusUnwantedEvent** para impedir que as notificações subsequentes.  
  
 *pConnection*  
 Um [Conexão](../../../ado/reference/ado-api/connection-object-ado.md) objeto. A conexão para a qual o aviso ocorreu. Por exemplo, os avisos podem ocorrer ao abrir um **Conexão** objeto ou executar um [comando](../../../ado/reference/ado-api/command-object-ado.md) em uma **Conexão**.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de modelo de eventos do ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Resumo de manipulador de eventos de ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Objeto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)