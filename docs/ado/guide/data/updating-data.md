---
title: Atualizando dados | Microsoft Docs
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
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9979faafbccf87f2e410da7708b67d841fbf347
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data"></a>Atualizando dados
Comportamento de atualização e a funcionalidade depende em grande parte atualizar modo (tipo de bloqueio), o tipo de cursor e o local do cursor.  
  
 Use o **atualização** método para salvar as alterações feitas no registro atual de um **conjunto de registros** objeto desde a chamada a **AddNew** método ou desde alterar quaisquer valores de campo um registro existente. O **registros** objeto deve dar suporte a atualizações.  
  
 Se o **registros** objeto oferece suporte a atualização em lotes, você pode armazenar em cache várias alterações para um ou mais registros localmente até que você chame o **UpdateBatch** método. Se você estiver editando o registro atual ou adicionar um novo registro, quando você chama o **UpdateBatch** método ADO automaticamente chamará o **atualização** método para salvar as alterações pendentes para o registro atual antes de transmitir as alterações em lotes para o provedor.  
  
 O registro atual permanece atual depois de chamar o **atualização** ou **UpdateBatch** métodos.  
  
 Esta seção contém os tópicos a seguir.  
  
-   [Modo imediato](../../../ado/guide/data/immediate-mode.md)  
  
-   [Modo de lote](../../../ado/guide/data/batch-mode.md)  
  
-   [Processamento de transações](../../../ado/guide/data/transaction-processing.md)
