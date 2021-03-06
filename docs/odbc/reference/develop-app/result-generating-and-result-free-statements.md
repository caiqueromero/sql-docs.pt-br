---
title: Instruções de geração de resultado e liberar resultados | Microsoft Docs
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
- result-generating statements [ODBC]
- batches [ODBC], result-generating statements
- batches [ODBC], result-free statements
- SQL statements [ODBC], batches
- result-free statements [ODBC]
ms.assetid: 2f3475d1-3999-4dd8-aba2-a6e1299c95f8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d314aa68c02a227f84e6785b722f44dd68964d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="result-generating-and-result-free-statements"></a>Instruções de geração de resultado e liberar resultados
Instruções SQL podem ser livremente divididas em cinco categorias a seguir:  
  
-   **Resultados de geração de conjunto de instruções** essas são instruções SQL que geram um conjunto de resultados. Por exemplo, um **selecione** instrução.  
  
-   **Instruções de geração de contagem de linhas** essas são instruções SQL que geram uma contagem de linhas afetadas. Por exemplo, um **atualização** ou **excluir** instrução.  
  
-   **Data Definition Language (DDL) instruções** essas são instruções SQL que modificam a estrutura do banco de dados. Por exemplo, **CREATE TABLE** ou **DROP INDEX**.  
  
-   **Instruções de alteração de contexto** essas são instruções SQL que alterar o contexto de um banco de dados. Por exemplo, o **USE** e **definir** instruções no SQL Server.  
  
-   **Instruções administrativas** essas são instruções SQL usado para fins administrativos em um banco de dados. Por exemplo, **GRANT** e **REVOGAR**.  
  
 Instruções SQL nas duas primeiras categorias são coletivamente conhecidas como *instruções geram resultados*. Instruções SQL em três categorias de segundo são coletivamente conhecidas como *livre resultados de instruções*. ODBC define a semântica de lotes que incluem as instruções somente gerar resultados. Essa semântica variar muito e, portanto, específico de fonte de dados. Por exemplo, o driver do SQL Server não dá suporte a descartar um objeto e, em seguida, referindo-se a ou recriando o mesmo objeto no mesmo lote. Portanto, o termo *lote* como usado nesse manual refere-se somente a lotes de geração de resultado instruções.
