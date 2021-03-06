---
title: os_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b800dc110baa7279edb2ce788befb433b7afd77a
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmostasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retorna uma linha para cada tarefa que está ativa na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Para chamar essa de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use o nome **sys.dm_pdw_nodes_os_tasks**.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Endereço de memória do objeto.|  
|**task_state**|**nvarchar(60)**|O estado da tarefa. Pode ser um dos seguintes:<br /><br /> PENDING: Esperando por um thread de trabalho.<br /><br /> RUNNABLE: Executável, mas esperando receber um quantum.<br /><br /> RUNNING: Atualmente em execução no agendador.<br /><br /> SUSPENDED: Tem um trabalhador, mas está esperando por um evento.<br /><br /> DONE: Concluído.<br /><br /> SPINLOOP: Preso em um spinlock.|  
|**context_switches_count**|**Int**|Número de alternâncias de contexto de agendador que esta tarefa completou.|  
|**pending_io_count**|**Int**|Número de E/Ss físicas executadas por esta tarefa.|  
|**pending_io_byte_count**|**bigint**|Contagem total de bytes de E/Ss que são executadas por esta tarefa.|  
|**pending_io_byte_average**|**Int**|Contagem média de bytes de E/Ss que são executadas por esta tarefa.|  
|**scheduler_id**|**Int**|ID do agendador pai. Este é um identificador das informações de agendador para esta tarefa. Para obter mais informações, consulte [sys.DM os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|**session_id**|**smallint**|ID da sessão que está associado à tarefa.|  
|**exec_context_id**|**Int**|ID do contexto de execução que está associado à tarefa.|  
|**request_id**|**Int**|ID da solicitação da tarefa. Para obter mais informações, consulte [exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|**worker_address**|**varbinary(8)**|Endereço de memória do trabalhador que está executando a tarefa.<br /><br /> NULL = A tarefa está esperando que um trabalhador possa ser executado ou a execução da tarefa foi recém-concluída.<br /><br /> Para obter mais informações, consulte [sys.DM os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|**host_address**|**varbinary(8)**|Endereço de memória do host.<br /><br /> 0 = A hospedagem não foi usada para criar a tarefa. Isto ajuda a identificar o host que foi usado para criar esta tarefa.<br /><br /> Para obter mais informações, consulte [sys.DM os_host &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md).|  
|**parent_task_address**|**varbinary(8)**|Endereço de memória da tarefa que é pai do objeto.|  
|**pdw_node_id**|**Int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> O identificador para o nó que essa distribuição é no.|  
  
## <a name="permissions"></a>Permissões

Em [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requer o `VIEW DATABASE STATE` no banco de dados.   

## <a name="examples"></a>Exemplos  
  
### <a name="a-monitoring-parallel-requests"></a>A. Monitorando solicitações paralelas  
 Para solicitações que são executadas em paralelo, você verá várias linhas para a mesma combinação de (\<**session_id**>, \< **request_id**>). Use a consulta a seguir para localizar o [configurar o grau máximo de paralelismo opção de configuração do servidor](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) para todas as solicitações ativas.  
  
> [!NOTE]  
>  Um **request_id** é exclusivo dentro de uma sessão.  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>B. Associando IDs de sessão a threads do Windows  
 Você pode usar a consulta a seguir para associar um valor de ID de sessão a um ID de thread do Windows. Depois, poderá monitorar o desempenho do thread no Monitor de Desempenho do Windows. A consulta a seguir não retorna informações de sessões que estão suspensas.  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
  [Sistema operacional SQL Server relacionadas exibições de gerenciamento dinâmico &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


