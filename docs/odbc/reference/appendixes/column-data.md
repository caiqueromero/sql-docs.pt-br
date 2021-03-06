---
title: Dados da coluna | Microsoft Docs
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
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 428f7c4a9d0e21cb989721b095b65bf0c48306fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="column-data"></a>Dados de coluna
> [!IMPORTANT]  
>  Este recurso será removido em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. A Microsoft recomenda o uso da funcionalidade de cursor do driver.  
  
 A biblioteca de cursores cria um buffer em cache para cada buffer de dados associado ao conjunto de resultados com **SQLBindCol**. Ele usa os valores nesses buffers para construir um **onde** cláusula quando emula um posicionadas instrução update ou delete. Ele atualiza esses buffers dos buffers de linhas quando ele busca dados da fonte de dados e quando ele executa instruções update posicionadas.  
  
 Quando a biblioteca de cursores atualiza seu cache dos buffers de conjunto de linhas, ele transfere os dados de acordo com o tipo de dados C especificado em **SQLBindCol**. Por exemplo, se o tipo de dados C de um buffer de linhas for SQL_C_SLONG, a biblioteca de cursores transferências de quatro bytes de dados. Se for SQL_C_CHAR e *BufferLength* é 10, a biblioteca de cursores transfere 10 bytes de dados. A biblioteca de cursores não executa nenhuma verificação de tipo ou conversões nos dados transfere.  
  
> [!NOTE]  
>  A biblioteca de cursores não atualiza o cache para uma coluna se **StrLen_or_IndPtr* no conjunto de linhas correspondente buffer é o resultado da macro SQL_LEN_DATA_AT_EXEC ou SQL_DATA_AT_EXEC.  
  
 Quando atualiza uma coluna, uma fonte em branco preenche caracteres de comprimento fixo de dados e dados binários de comprimento fixo de zero preenche conforme necessário. Por exemplo, uma fonte de dados armazena "Smith" em uma coluna char (10) como "Smith". A biblioteca de cursores não dados não o preenchimento de espaço em branco ou o preenchimento de zero nos buffers de linhas quando ele copia esses dados para seu cache depois de executar uma instrução update posicionadas. Portanto, se um aplicativo requer que os valores no cache da biblioteca de cursor são convertidas em branco ou sem preenchimento, ele deverá painel de espaço em branco ou painel de zero os valores nos buffers de linhas antes de executar uma instrução update posicionadas.
