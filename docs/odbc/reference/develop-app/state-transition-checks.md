---
title: Verificações de transição de estado | Microsoft Docs
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
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23f2b87fc943535075e1456bb31366ff9667b07b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="state-transition-checks"></a>Verificações de transição de estado
O Gerenciador de Driver verifica se o estado do ambiente, conexão ou instrução é apropriado para a função que está sendo chamada. Por exemplo, uma conexão deve estar em um alocado de estado quando **SQLConnect** é chamado; uma instrução deve estar em um preparada estado quando **SQLExecute** é chamado. O Gerenciador de Driver retornará SQL_ERROR para erros de transição de estado.
