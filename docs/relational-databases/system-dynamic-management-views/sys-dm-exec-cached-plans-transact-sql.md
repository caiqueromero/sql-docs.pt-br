---
title: exec_cached_plans (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cached_plans
- dm_exec_cached_plans
- dm_exec_cached_plans_TSQL
- sys.dm_exec_cached_plans_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_cached_plans dynamic management view
ms.assetid: 95b707d3-3a93-407f-8e88-4515d4f2039d
caps.latest.revision: "44"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 816fcb7a7fbf362f2f531b93629508ab3ab2b76f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexeccachedplans-transact-sql"></a>sys.dm_exec_cached_plans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna uma linha para cada plano de consulta armazenado em cache pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a fim de acelerar a execução da consulta. É possível usar esta exibição de gerenciamento dinâmico para localizar planos de consulta em cache, texto de consulta em cache, a quantidade de memória usada pelos planos em cache e o número de reutilizações dos planos em cache.  
  
 No [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], as exibições de gerenciamento dinâmico não podem expor informações que afetarão a contenção do banco de dados ou informações sobre outros bancos de dados aos quais o usuário tem acesso. Para evitar a exposição dessas informações, cada linha que contém os dados que não pertencem ao locatário conectado será filtrada. Além disso, os valores nas colunas **memory_object_address** e **pool_id** são filtrados; o valor da coluna é definido como NULL.  
  
> [!NOTE]  
>  Para chamar essa de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use o nome **sys.dm_pdw_nodes_exec_cached_plans**.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|bucketid|**int**|ID do segmento de hash em que a entrada é armazenada em cache. O valor indica um intervalo de 0 ao tamanho de tabela de hash para o tipo de cache.<br /><br /> Para os caches de planos SQL e planos de objeto, o tamanho da tabela de hash pode ser de até 10007 em sistemas de 32 bits e até 40009 em sistemas de 64 bits. Para os caches de árvores associadas, o tamanho da tabela de hash pode ser de até 1009 em sistemas de 32 bits e até 4001 em sistemas de 64 bits. Para os caches de procedimentos armazenados estendidos, o tamanho da tabela de hash pode ser de até 127 em sistemas de 32 e 64 bits.|  
|refcounts|**int**|Número de objetos de cache que fazem referência a este objeto de cache. **Refcounts** deve ser pelo menos 1 para uma entrada fique no cache.|  
|usecounts|**int**|Número de vezes que o objeto de cache foi examinado. Não incrementado quando consultas parametrizadas localizam um plano no cache. Pode ser incrementado várias vezes durante o us do plano de execução.|  
|size_in_bytes|**int**|Número de bytes consumidos pelo objeto de cache.|  
|memory_object_address|**varbinary (8)**|Endereço de memória da entrada em cache. Esse valor pode ser usado com [sys.DM os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md) para obter a análise de memória do plano de cache e com [sys.DM os_memory_cache_entries](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)entradas para obter o custo de armazenamento em cache a entrada.|  
|cacheobjtype|**nvarchar(34)**|Tipo de objeto no cache. O valor pode ser um dos seguintes:<br /><br /> Compiled Plan<br /><br /> Compiled Plan Stub<br /><br /> Parse Tree<br /><br /> Extended Proc<br /><br /> CLR Compiled Func<br /><br /> CLR Compiled Proc|  
|objtype|**nvarchar(16)**|Tipo de objeto. Abaixo estão os valores possíveis e suas descrições correspondentes.<br /><br /> Processo: Procedimento armazenado<br />Preparado: Instrução preparada<br />Adhoc: de consulta Ad hoc. Refere-se ao [!INCLUDE[tsql](../../includes/tsql-md.md)] enviado como eventos de linguagem usando **osql** ou **sqlcmd** em vez de chamadas de procedimento remoto.<br />ReplProc: Filtro de procedimento de replicação<br />Gatilho: gatilho<br />Modo de exibição: modo de exibição<br />Padrão: padrão<br />UsrTab: Tabela de usuário<br />SysTab: Tabela do sistema<br />Verificação: Restrição de verificação<br />Regra: regra|  
|plan_handle|**varbinary(64)**|Identificador do plano na memória. Esse identificador é transitório e permanece constante somente enquanto o plano permanece no cache. Este valor pode ser usado com as seguintes funções de gerenciamento dinâmico:<br /><br /> [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)<br /><br /> [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)<br /><br /> [sys.dm_exec_plan_attributes](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)|  
|pool_id|**int**|ID do pool de recursos no qual o uso de memória do plano é contabilizado.|  
|pdw_node_id|**int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> O identificador para o nó que essa distribuição é no.|  
  
 <sup>1</sup>  
  
## <a name="permissions"></a>Permissões  
 Em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requer a permissão VIEW SERVER STATE no servidor.  
  
 Em [!INCLUDE[ssSDS](../../includes/sssds-md.md)] camadas Premium requer a permissão VIEW DATABASE STATE no banco de dados. Em [!INCLUDE[ssSDS](../../includes/sssds-md.md)] camadas Standard e Basic requer o [!INCLUDE[ssSDS](../../includes/sssds-md.md)] conta de administrador.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-returning-the-batch-text-of-cached-entries-that-are-reused"></a>A. Retornando o texto de lote de entradas em cache que são reutilizadas  
 O exemplo seguinte retorna o texto SQL de todas as entradas em cache que foram usadas mais de uma vez.  
  
```  
SELECT usecounts, cacheobjtype, objtype, text   
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_sql_text(plan_handle)   
WHERE usecounts > 1   
ORDER BY usecounts DESC;  
GO  
```  
  
### <a name="b-returning-query-plans-for-all-cached-triggers"></a>B. Retornando planos de consulta para todos os gatilhos em cache  
 O exemplo seguinte retorna os planos de consulta de todos os gatilhos em cache.  
  
```  
SELECT plan_handle, query_plan, objtype   
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_query_plan(plan_handle)   
WHERE objtype ='Trigger';  
GO  
```  
  
### <a name="c-returning-the-set-options-with-which-the-plan-was-compiled"></a>C. Retornando as opções SET com que o plano foi compilado  
 O exemplo seguinte retorna as opções SET com que o plano foi compilado. O `sql_handle` do plano também é retornado. O operador PIVOT é usado para a saída de `set_options` e `sql_handle` atributos como colunas em vez de linhas. Para obter mais informações sobre o valor retornado em `set_options`, consulte [sys.DM exec_plan_attributes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md).  
  
```  
SELECT plan_handle, pvt.set_options, pvt.sql_handle  
FROM (  
      SELECT plan_handle, epa.attribute, epa.value   
      FROM sys.dm_exec_cached_plans   
      OUTER APPLY sys.dm_exec_plan_attributes(plan_handle) AS epa  
      WHERE cacheobjtype = 'Compiled Plan'  
      ) AS ecpa   
PIVOT (MAX(ecpa.value) FOR ecpa.attribute IN ("set_options", "sql_handle")) AS pvt;  
GO  
```  
  
### <a name="d-returning-the-memory-breakdown-of-all-cached-compiled-plans"></a>D. Retornando a análise de memória de todos os planos compilados em cache  
 O exemplo seguinte retorna uma análise da memória usada por todos os planos compilados no cache.  
  
```  
SELECT plan_handle, ecp.memory_object_address AS CompiledPlan_MemoryObject,   
    omo.memory_object_address, pages_allocated_count, type, page_size_in_bytes   
FROM sys.dm_exec_cached_plans AS ecp   
JOIN sys.dm_os_memory_objects AS omo   
    ON ecp.memory_object_address = omo.memory_object_address   
    OR ecp.memory_object_address = omo.parent_address  
WHERE cacheobjtype = 'Compiled Plan';  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [Exibições e funções de gerenciamento dinâmico &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funções e exibições de gerenciamento dinâmico &#40; relacionadas à execução Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.DM exec_query_plan &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)   
 [sys.DM exec_plan_attributes &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)   
 [sys.DM exec_sql_text &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.DM os_memory_objects &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)   
 [sys.DM os_memory_cache_entries &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)  
  
  

