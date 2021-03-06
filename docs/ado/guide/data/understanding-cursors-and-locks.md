---
title: Noções básicas sobre cursores e bloqueios | Microsoft Docs
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
- locks [ADO]
- cursors [ADO]
ms.assetid: c1b7d7e6-1707-4ce2-863f-0c6dea967df6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b9c31b958efd4510fc7def4c15294c674ee031b5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-cursors-and-locks"></a>Noções básicas sobre cursores e bloqueios
É importante entender como os cursores operam para que você pode selecionar o tipo de cursor melhor e mais eficiente para requisitos de acesso a dados do aplicativo. Uma configuração menor ideal do cursor pode tornar lenta lamentavelmente de operações de acesso a dados.  
  
 Muitos recursos do ADO **registros** objeto são determinados pelo tipo e local do cursor, bem como o tipo de bloqueio.  
  
 Esta seção contém os tópicos a seguir.  
  
-   [O que é um cursor?](../../../ado/guide/data/what-is-a-cursor.md)  
  
-   [Tipos de cursor](../../../ado/guide/data/types-of-cursors-ado.md)  
  
-   [A importância da posição do cursor](../../../ado/guide/data/the-significance-of-cursor-location.md)  
  
-   [O Microsoft Cursor Service para OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md)  
  
-   [O que é um bloqueio?](../../../ado/guide/data/what-is-a-lock.md)  
  
-   [Usando CacheSize](../../../ado/guide/data/using-cachesize.md)  
  
-   [Características de cursor e de bloqueio](../../../ado/guide/data/cursor-and-lock-characteristics.md)
