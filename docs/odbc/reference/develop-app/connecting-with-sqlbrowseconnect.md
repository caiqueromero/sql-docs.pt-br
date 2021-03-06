---
title: Conectando com SQLBrowseConnect | Microsoft Docs
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
- connecting to driver [ODBC], SQLBrowseConnect
- SQLBrowseConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLBrowseConnect
ms.assetid: 6c2e9f76-b766-48df-b109-246bb05ae45d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 573c0f1cef639c41b4c03c6dbae4a7c9b8858cf4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-with-sqlbrowseconnect"></a>Conectando com SQLBrowseConnect
**SQLBrowseConnect**, como **SQLDriverConnect**, usa uma cadeia de caracteres de conexão. No entanto, usando **SQLBrowseConnect**, um aplicativo pode construir uma cadeia de caracteres de conexão completa em tempo de execução. Isso permite que o aplicativo faça duas tarefas:  
  
-   Criar suas próprias caixas de diálogo para solicitar essas informações, assim mantendo o controle "de aparência."  
  
-   Procure no sistema por fontes de dados que possam ser usadas por um driver específico, possivelmente em várias etapas. Por exemplo, primeiro o usuário pode procurar servidores na rede e, depois de escolher um, procurar no servidor pelos bancos de dados acessíveis pelo driver.  
  
 O aplicativo chama **SQLBrowseConnect** e passa uma cadeia de caracteres de conexão, conhecida como o *procurar a cadeia de caracteres de conexão de solicitação,* que especifica uma driver ou fonte de dados. O driver retorna uma cadeia de caracteres de conexão, conhecida como o *procurar a cadeia de caracteres de conexão do resultado,* que contém as palavras-chave, os valores possíveis (se a palavra-chave aceita um conjunto separado de valores) e nomes amigáveis. O aplicativo cria uma caixa de diálogo com os nomes amigáveis e solicita ao usuário para valores. Em seguida, cria uma nova cadeia de conexão de solicitação de procurar entre esses valores e retornará para o driver com outra chamada para **SQLBrowseConnect**.  
  
 Como cadeias de caracteres de conexão são passadas de e para trás, o driver pode fornecer vários níveis de navegação, retornando uma nova cadeia de caracteres de conexão quando o aplicativo retorna antigo. Por exemplo, a primeira vez que um aplicativo chama **SQLBrowseConnect**, o driver pode retornar palavras-chave para solicitar ao usuário um nome de servidor. Quando o aplicativo retorna o nome do servidor, o driver pode retornar palavras-chave para solicitar ao usuário para um banco de dados. O processo de localização seria concluído depois que o aplicativo retornado o nome do banco de dados.  
  
 Cada vez que **SQLBrowseConnect** retorna uma nova cadeia de conexão de resultado procurar, ele retorna SQL_NEED_DATA como seu código de retorno. Isso informa o aplicativo que o processo de conexão não foi concluído. Até **SQLBrowseConnect** retorna SQL_SUCCESS, a conexão está em um estado de dados necessário e não pode ser usado para outras finalidades, como definir um atributo de conexão. O aplicativo pode encerrar a conexão navegação processo chamando **SQLDisconnect**.  
  
 Esta seção contém o tópico a seguir.  
  
-   [Exemplo de navegação do SQL Server](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
