---
title: SQLGetData (biblioteca de Cursor) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2c3e1edf4d37dd49941b5c019d3337eaee5b706
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (biblioteca de Cursor)
> [!IMPORTANT]  
>  Este recurso será removido em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. A Microsoft recomenda o uso da funcionalidade de cursor do driver.  
  
 Este tópico discute o uso do **SQLGetData** função na biblioteca de cursor. Para obter informações gerais sobre **SQLGetData**, consulte [função SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 A biblioteca de cursores implementa **SQLGetData** criando primeiro uma **selecione** instrução com uma **onde** cláusula que enumera os valores armazenados no cache de cada limite coluna na linha atual. Em seguida, executa o **selecione** instrução selecionar novamente a linha e chama **SQLGetData** no driver para recuperar os dados da fonte de dados (em vez de cache).  
  
> [!CAUTION]  
>  O **onde** cláusula construída pela biblioteca de cursores para identificar a linha atual pode não conseguir identificar todas as linhas, identificar uma linha diferente ou identificar mais de uma linha. Para obter mais informações, consulte [construindo instruções pesquisados](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Se o atributo da instrução SQL_ATTR_USE_BOOKMARKS for definido como SQL_UB_VARIABLE, **SQLGetData** pode ser chamado na coluna 0 para retornar dados de indicador.  
  
 Chamadas para **SQLGetData** estão sujeitas às seguintes restrições:  
  
-   **SQLGetData** não pode ser chamado para cursores de somente avanço.  
  
-   **SQLGetData** pode ser chamado apenas quando as seguintes condições forem atendidas: um **selecione** instrução gerou o conjunto de resultados; o **selecione** instrução não continha uma junção, um  **União** cláusula, ou um **GROUP BY** cláusula; e as colunas que é usado um alias ou uma expressão na lista de seleção não foram vinculados com **SQLBindCol**.  
  
-   Se o driver oferece suporte a apenas uma instrução ativa, a biblioteca de cursores busca o restante do conjunto de resultados antes de executar o **selecione** instrução e chamar **SQLGetData**.
