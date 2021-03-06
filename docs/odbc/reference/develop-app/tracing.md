---
title: Rastreamento | Microsoft Docs
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
- tracing options [ODBC], about tracing
- driver manager [ODBC], tracing
ms.assetid: 77ed4c6c-d976-4eb2-8526-a12697b0ef83
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ff139b0074a22adc14903174ec031cd4176dca6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="tracing"></a>Rastreamento
O Gerenciador de Driver ODBC tem um recurso de rastreamento que permite que a sequência de chamadas de função feitas por um aplicativo ODBC a ser registrada e transcrita em um arquivo de log. O rastreamento é executado por uma DLL de rastreamento que captura chamadas entre o aplicativo e o Gerenciador de Driver e entre o Gerenciador de Driver e o driver. Esse método de rastreamento substitui o rastreamento executado pelo ODBC 2 *. x* Gerenciador de Driver e o rastreamento realizadas em ODBC 2 *. x* por Spy ODBC.  
  
 Esta seção contém os tópicos a seguir.  
  
-   [DLL de rastreamento](../../../odbc/reference/develop-app/trace-dll.md)  
  
-   [Arquivo de rastreamento](../../../odbc/reference/develop-app/trace-file.md)  
  
-   [Habilitando o rastreamento](../../../odbc/reference/develop-app/enabling-tracing.md)  
  
-   [Rastreamento dinâmico](../../../odbc/reference/develop-app/dynamic-tracing.md)
