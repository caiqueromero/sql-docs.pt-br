---
title: Identificadores de tipo SQL | Microsoft Docs
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
- data types [ODBC], identifiers
- SQL data types [ODBC], identifiers
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f3a9270e698f7f0ff12bd12c02de865a3c6f2b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sql-type-identifiers"></a>Identificadores de tipo SQL
Cada fonte de dados define seus próprios tipos de dados SQL. ODBC define identificadores de tipo e descreve as características gerais dos tipos de dados SQL que podem ser mapeados para cada identificador de tipo. É específico do driver como cada tipo de dados na fonte de dados subjacente é mapeado para um identificador de tipo SQL do ODBC.  
  
 Por exemplo, SQL_CHAR é o identificador de tipo para uma coluna de caracteres com um comprimento fixo, geralmente entre 1 e 254 caracteres. Essas características correspondem ao tipo de dados CHAR encontrado em várias fontes de dados do SQL. Portanto, quando um aplicativo detecta que o identificador de tipo de uma coluna é SQL_CHAR, ele pode assumir que provavelmente está lidando com uma coluna CHAR. No entanto, ainda deve verificar o tamanho em bytes da coluna antes de assumir que ele está entre 1 e 254 caracteres. o driver para uma fonte de dados não SQL, por exemplo, pode mapear uma coluna de caracteres de comprimento fixo de 500 caracteres para SQL_CHAR ou SQL_LONGVARCHAR, porque não é uma correspondência exata.  
  
 ODBC define uma ampla variedade de identificadores de tipo SQL. No entanto, o driver não é necessário usar todos esses identificadores. Em vez disso, ele usa apenas os identificadores que ele precisa expor os tipos de dados do SQL com suporte pela fonte de dados subjacente. Se a fonte de dados subjacente oferece suporte a tipos de dados SQL para que nenhum identificador de tipo correspondente, o driver pode definir identificadores de tipo adicionais. Para obter mais informações, consulte [tipos de dados específicos do Driver, tipos de descritor, tipos de informações, tipos de diagnóstico e atributos](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Para obter uma descrição completa de identificadores de tipo SQL, consulte [tipos de dados C](../../../odbc/reference/appendixes/c-data-types.md) no Apêndice d: os tipos de dados.
