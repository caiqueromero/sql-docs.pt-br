---
title: Controle de simultaneidade | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2fd05a84e70b601180ce67a94cbdc4caabf7e37e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="concurrency-control"></a>Controle de simultaneidade
*Simultaneidade* é a capacidade de duas transações para usar os mesmos dados ao mesmo tempo, e com a transação maior isolamento normalmente vem redução de simultaneidade. Isso ocorre porque o isolamento de transação geralmente é implementado pelo bloqueio de linhas, e que mais linhas são bloqueadas, poucas transações podem ser concluídas sem serem bloqueados pelo menos temporariamente por uma linha bloqueada. Enquanto a redução de simultaneidade é aceita normalmente como uma compensação para os níveis mais altos de isolamento de transação necessários para manter a integridade do banco de dados, ele pode se tornar um problema em aplicativos interativos com atividade de leitura/gravação alta que usar cursores.  
  
 Por exemplo, suponha que um aplicativo executa a instrução SQL **selecione \* de pedidos**. Ele chama **SQLFetchScroll** para rolar o resultado definido e permite ao usuário atualizar, excluir ou inserir ordens. Depois que o usuário atualiza, exclui ou insere um pedido, o aplicativo confirma a transação.  
  
 Se o nível de isolamento for Repeatable Read, a transação pode — dependendo de como ele é implementado — bloquear cada linha retornada por **SQLFetchScroll**. Se o nível de isolamento é Serializable, a transação pode bloquear a tabela inteira de pedidos. Em ambos os casos, a transação libera seus bloqueios somente quando ele for confirmado ou revertido. Assim, se o usuário gasta muito tempo lendo pedidos e muito pouco tempo, atualizar, excluir ou inseri-los, a transação pode facilmente bloquear um grande número de linhas, tornando-os disponíveis para outros usuários.  
  
 Isso é um problema, mesmo se o cursor é somente leitura e o aplicativo permite que o usuário leia apenas pedidos existentes. Nesse caso, o aplicativo confirma a transação e libera os bloqueios, quando ele chama **SQLCloseCursor** (no modo de confirmação automática) ou **SQLEndTran** (no modo de confirmação manual).  
  
 Esta seção contém os tópicos a seguir.  
  
-   [Tipos de simultaneidade](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [Simultaneidade otimista](../../../odbc/reference/develop-app/optimistic-concurrency.md)
