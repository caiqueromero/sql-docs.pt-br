---
title: "Enviar as atualizações: método UpdateBatch | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87123797-831f-48e0-94b5-f669f9ca194a
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6cad1bfd63ffafd32d0621f6142717cd7175ccd0
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="sending-the-updates-updatebatch-method"></a>Enviar as atualizações: método UpdateBatch
O código a seguir abre um conjunto de registros em modo de lote, definindo a propriedade LockType adLockBatchOptimistic e CursorLocation para adUseClient. Adiciona dois novos registros e altera o valor de um campo em um registro existente, salvar os valores originais e, em seguida, chama UpdateBatch para enviar que as alterações de volta para a fonte de dados.  
  
## <a name="remarks"></a>Comentários  
  
```  
'BeginBatchUpdate  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT ShipperId, CompanyName, Phone FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    ' Send the updates  
    objRs1.UpdateBatch  
'EndBatchUpdate  
```  
  
 Se você estiver editando o registro atual ou adicionar um novo registro, quando você chama o método UpdateBatch, ADO automaticamente chamar o método de atualização para salvar as alterações pendentes para o registro atual antes de transmitir as alterações em lotes para o provedor.  
  
## <a name="see-also"></a>Consulte também  
 [Modo de lote](../../../ado/guide/data/batch-mode.md)