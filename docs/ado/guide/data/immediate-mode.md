---
title: Modo imediato | Microsoft Docs
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
helpviewer_keywords:
- data updates [ADO], immediate mode
- immediate mode [ADO]
- updating data [ADO], immediate mode
ms.assetid: 31fc53d0-97de-4315-a87b-3bf5cdd1f432
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6acd34e06c4660cff3e90c8ef2dd760996d77259
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="immediate-mode"></a>Modo imediato
Modo imediato está em vigor quando o **LockType** está definida como **adLockOptimistic** ou **adLockPessimistic**. No modo imediato, as alterações em um registro são propagadas para a fonte de dados assim que você declarar o trabalho em uma linha completa chamando o **atualização** método.  
  
## <a name="calling-update"></a>Chamada de atualização  
 Se você mover de registro estiver adicionando ou editando antes de chamar o **atualização** , ADO será automaticamente da chamada do método **atualização** para salvar as alterações. Você deve chamar o **CancelUpdate** método antes de navegação se você deseja cancelar as alterações feitas no registro atual ou descartar um registro recém-adicionada.  
  
 O registro atual permanece atual depois de chamar o **atualização** método.  
  
## <a name="cancelupdate"></a>CancelUpdate  
 Use o **CancelUpdate** método para cancelar as alterações feitas na linha atual ou para descartar uma linha adicionada recentemente. Você não pode cancelar as alterações para a linha atual ou uma nova linha depois de chamar o **atualização** método, a menos que as alterações são parte de uma transação que é possível revertê-lo com o **RollbackTrans** método ou parte de uma atualização em lotes. No caso de uma atualização em lotes, você pode cancelar o **atualizar** com o **CancelUpdate** ou **CancelBatch** método.  
  
 Se você estiver adicionando uma nova linha ao chamar o **CancelUpdate** método, a linha atual se tornará a linha atual antes do **AddNew** chamar.  
  
 Se você não alterou a linha atual ou adicionou uma nova linha, chamar o **CancelUpdate** método gera um erro.
