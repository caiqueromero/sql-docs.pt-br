---
title: Interoperabilidade | Microsoft Docs
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
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 486bfc2b144e8b228197b7b813af7aaebfe5b837
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="interoperability"></a>Interoperabilidade
*Interoperabilidade* é a capacidade de um único aplicativo para operar com muitos DBMSs diferentes. A necessidade de escrever aplicativos interoperáveis genéricos foi um dos principais fatores que levam ao desenvolvimento de ODBC. No entanto, a interoperabilidade não é um caminho simple seguido de "não interoperável" para "completamente interoperável". O caminho tem muitas ramificações e cada requer que as variações de recursos, a velocidade, a complexidade de código e tempo de desenvolvimento.  
  
 O processo de criar um aplicativo interoperável segue várias etapas:  
  
1.  Decidir se o aplicativo irá usar o ODBC.  
  
2.  Escolhendo um nível de interoperabilidade e decidir quais compensações são necessárias para atingir esse nível.  
  
3.  Escrevendo código interoperável e testá-lo como totalmente.  
  
 Deve-se observar que a interoperabilidade é principalmente o domínio do gravador de aplicativos. Drivers são projetados para trabalhar com um único DBMS e, por definição, não são interoperáveis. Eles têm um papel na interoperabilidade implementando corretamente e expondo ODBC em um único DBMS.  
  
 Esta seção contém os tópicos a seguir.  
  
-   [ODBC é a resposta?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Escolhendo um nível de interoperabilidade](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Determinando os drivers e DBMSs de destino](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Considerando os recursos de banco de dados a serem usados](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Comprimento do ciclo do produto](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Escrevendo um aplicativo interoperável](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Testando aplicativos interoperáveis](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
