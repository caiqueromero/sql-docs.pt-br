---
title: Modos de exibição de esquema | Microsoft Docs
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
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 686b13ff9b480a1e2e96a175fe546d064079d871
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="schema-views"></a>Exibições do esquema
Um aplicativo pode recuperar informações de metadados do DBMS chamando funções de catálogo ODBC ou por meio de exibições INFORMATION_SCHEMA. As exibições são definidas pelo padrão ANSI SQL-92.  
  
 Se o DBMS e suporte de driver, as exibições INFORMATION_SCHEMA fornecem um meio de mais poderoso e abrangente de recuperação de metadados que fornecem as funções de catálogo ODBC. Um aplicativo pode executar seu próprio personalizado **selecione** instrução em relação a um desses modos de exibição, pode unir as exibições, ou pode executar uma união em modos de exibição. Ao oferecer maior do utilitário e uma maior variedade de metadados, exibições INFORMATION_SCHEMA não têm suporte com frequência pelo DBMS. Isso pode ser alterado conforme mais DBMSs e drivers de alcançar a conformidade com o SQL-92.  
  
 Para determinar quais modos de exibição têm suporte, um aplicativo chama **SQLGetInfo** com a opção SQL_INFO_SCHEMA_VIEWS. Para recuperar metadados de um modo de exibição com suporte, o aplicativo executa um **selecione** instrução que especifica as informações de esquema necessárias.
