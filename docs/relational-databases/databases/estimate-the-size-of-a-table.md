---
title: Estimar o tamanho de uma tabela | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2e36482008cdbd32cfd11c1c8f49f330ee606f77
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="estimate-the-size-of-a-table"></a>Estimar o tamanho de uma tabela
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Você pode usar as seguintes etapas para estimar a quantidade de espaço necessária para armazenar dados em uma tabela:  
  
1.  Calcular o espaço necessário para o heap ou índice clusterizado seguindo as instruções em [Estimar o tamanho de um heap](../../relational-databases/databases/estimate-the-size-of-a-heap.md) ou [Estimar o tamanho de um índice clusterizado](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md).  
  
2.  Calcule o espaço necessário para cada índice não clusterizado, seguindo as instruções em [Estimar o tamanho de um índice não clusterizado](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Some os valores calculados nas etapas 1 e 2.  
  
## <a name="see-also"></a>Consulte Também  
 [Estimar o tamanho de um banco de dados](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [Estimar o tamanho de um heap](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Estimar o tamanho de um índice clusterizado](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Estimar o tamanho de um índice não clusterizado](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  
