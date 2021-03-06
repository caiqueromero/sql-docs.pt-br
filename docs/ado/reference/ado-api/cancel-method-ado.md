---
title: Cancelar o método (ADO) | Microsoft Docs
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
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9538bfe7e0c98cf89c052ba3244482def661ef3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="cancel-method-ado"></a>Método Cancel (ADO)
Cancela a execução de uma chamada de método assíncrono pendente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Remarks  
 Use o **Cancelar** método para finalizar a execução de uma chamada de método assíncrono: ou seja, um método invocado com o **adAsyncConnect**, **adAsyncExecute**, ou **adAsyncFetch** opção.  
  
 A tabela a seguir mostra qual tarefa foi finalizada quando você usa o **Cancelar** método em um determinado tipo de objeto.  
  
|Se *objeto* é um|A última chamada assíncrona para este método é finalizada|  
|----------------------|-------------------------------------------------------------|  
|[Comando](../../../ado/reference/ado-api/command-object-ado.md)|[Execute (executar)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Conexão](../../../ado/reference/ado-api/connection-object-ado.md)|[Executar](../../../ado/reference/ado-api/execute-method-ado-connection.md) ou [aberto](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Record](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [ExcluirRegistro](../../../ado/reference/ado-api/deleterecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md), ou [aberto](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|[Abrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Fluxo](../../../ado/reference/ado-api/stream-object-ado.md)|[Abrir](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>Aplica-se a  
  
||||  
|-|-|-|  
|[Objeto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Objeto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Objeto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Objeto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo do método Cancel (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Exemplo do método Cancel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Exemplo do método Cancel (VC + +)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Método Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Método CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Método CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Método CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Executar método (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Executar método (Conexão ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Método Open (Conexão ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Método Open (Conjunto de registros ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
