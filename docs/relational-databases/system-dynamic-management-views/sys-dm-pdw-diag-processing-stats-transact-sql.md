---
title: sys.dm_pdw_diag_processing_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 22c3a810349f1e41557572bd2bf5ce3ba25a7a27
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Exibe informações relacionadas a todos os eventos de diagnósticos internos que podem ser incorporados em sessões de diagnóstico definidas pelo administrador. Consulte essa exibição para entender as estatísticas por trás os subsistemas de eventos e de diagnóstico que a população de todos os outros DMVs de unidade. Há um grupo de filas para cada processo em cada nó.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**Int**|Esse log é de um nó de dispositivo.|  
|**process_id**|**Int**|Identificador do processo em execução enviar essa estatística.|  
|**target_name**|**nvarchar(255)**|O nome da fila.|  
|**queue_size**|**Int**|O número de itens na fila de processo. Geralmente, o tamanho da fila é 0. Um número positivo indica que o sistema está sob carga excessiva e está criando a lista de pendências de eventos. Uma contagem positiva nas outras colunas significa sistema está corrompido para essa fila determinada e DMVs relacionados.|  
|**lost_events_count**|**bigint**|O número de eventos perdidos.|  
  
## <a name="see-also"></a>Consulte também  
 [SQL Data Warehouse Parallel Data Warehouse e exibições de gerenciamento dinâmico &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
