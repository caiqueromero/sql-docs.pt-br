---
title: sys.DM db_file_space_usage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_file_space_usage
- sys.dm_db_file_space_usage_TSQL
- sys.dm_db_file_space_usage
- dm_db_file_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_file_space_usage dynamic management view
ms.assetid: 148a5276-a8d5-49d2-8146-3c63d24c2144
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 456c6bd1a7b83012d2791ec8340f98a06413b09f
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmdbfilespaceusage-transact-sql"></a>sys.dm_db_file_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retorna informações de uso do espaço de cada arquivo no banco de dados.  
  
> [!NOTE]  
>  Para chamar essa de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use o nome **sys.dm_pdw_nodes_db_file_space_usage**.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|ID do banco de dados.|  
|file_id|**smallint**|ID do arquivo.<br /><br /> file_id mapeia para file_id in [sys.DM io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md) e fileid em [Sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md).|  
|filegroup_id|**smallint**|**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> ID do grupo de arquivos.|  
|total_page_count|**bigint**|**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Número total de páginas no arquivo.|  
|allocated_extent_page_count|**bigint**|**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Número total de páginas nas extensões alocadas no arquivo.|  
|unallocated_extent_page_count|**bigint**|Número total de páginas nas extensões não alocadas no arquivo.<br /><br /> Páginas não utilizadas em extensões alocadas não são incluídas.|  
|version_store_reserved_page_count|**bigint**|Número total de páginas nas extensões uniformes alocadas para o repositório de versão. As páginas do repositório de versão nunca são alocadas de eventos mistos.<br /><br /> Páginas IAM não são incluídas, pois são sempre são alocadas de extensões mistas. As páginas PFS serão incluídas se forem alocadas de uma extensão uniforme.<br /><br /> Para obter mais informações, consulte [tran_version_store & #40; Transact-SQL & #41; ](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md).|  
|user_object_reserved_page_count|**bigint**|Número total de páginas alocadas de extensões uniformes para objetos de usuário no banco de dados. Páginas não usadas de uma extensão alocada são incluídas na contagem.<br /><br /> Páginas IAM não são incluídas, pois são sempre são alocadas de extensões mistas. As páginas PFS serão incluídas se forem alocadas de uma extensão uniforme.<br /><br /> Você pode usar a coluna total_pages no [allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) exibição para retornar a contagem de páginas reservadas de cada unidade de alocação no objeto de usuário do catálogo. No entanto, observe que a coluna total_pages inclui páginas IAM.|  
|internal_object_reserved_page_count|**bigint**|Número total de páginas nas extensões uniformes alocadas para objetos internos no arquivo. Páginas não usadas de uma extensão alocada são incluídas na contagem.<br /><br /> Páginas IAM não são incluídas, pois são sempre são alocadas de extensões mistas. As páginas PFS serão incluídas se forem alocadas de uma extensão uniforme.<br /><br /> Não há exibição do catálogo ou objeto de gerenciamento dinâmico que retorne a contagem de páginas de cada objeto interno.|  
|mixed_extent_page_count|**bigint**|Número total de páginas alocadas e não alocadas nas extensões mistas alocadas no arquivo. As extensões mistas contêm páginas alocadas a objetos diferentes. Essa contagem inclui todas as páginas IAM no arquivo.|
|modified_extent_page_count|**bigint**|**Aplica-se a:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 até [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br />Número total de páginas modificadas em alocados extensões do arquivo desde o último backup de banco de dados completo. A contagem de páginas modificadas pode ser usada para controlar a quantidade de alterações diferenciais do banco de dados desde o último backup completo, para decidir se o backup diferencial é necessária.|
|pdw_node_id|**Int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> O identificador para o nó que essa distribuição é no.|  
|distribution_id|**Int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> A id numérica exclusiva associada com a distribuição.|  
  
## <a name="remarks"></a>Remarks  
 As contagens de página estão sempre no nível de extensão. Portanto, os valores de contagem de página serão sempre um múltiplo de oito. As extensões que contêm páginas de alocação GAM (Global Alocação Map) e SGAM (Shared Global Allocation Map) são extensões uniformes alocadas. Elas não são incluídas nas contagens de página previamente descritas. Para obter mais informações sobre páginas e extensões, consulte [páginas e guia de arquitetura de extensões](../../relational-databases/pages-and-extents-architecture-guide.md). 
  
 O conteúdo do repositório de versão atual está no [tran_version_store](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md). As páginas de repositório de versão são controladas no nível de arquivo, em vez de no nível de sessão e tarefa, porque são recursos globais. Uma sessão pode gerar versões, mas as versões não podem ser removidas quando a sessão terminar. A limpeza total do repositório de versão deve considerar a transação mais longa em execução que exige acesso à versão particular. A transação de execução mais longa relacionada à versão repositório de limpeza pode ser descoberta visualizando a coluna elapsed_time_seconds em [sys.DM tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md).  
  
 Mudanças frequentes na coluna mixed_extent_page_count podem indicar uso pesado de páginas SGAM. Quando isso ocorrer, você poderá ver muitas esperas de PAGELATCH_UP nas quais o recurso de espera é uma página SGAM. Para obter mais informações, consulte [sys.DM os_waiting_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-waiting-tasks-transact-sql.md), [sys.DM os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md), e [sys.dm_os_latch_ estatísticas &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md).  
  
## <a name="user-objects"></a>Objetos do usuário  
 Os objetos a seguir são incluídos nos contadores de páginas de objeto do usuário:  
  
-   Tabelas e índices definidos pelo usuário  
  
-   Índices e tabelas do sistema  
  
-   Tabelas e índices temporários globais  
  
-   Tabelas e índices temporários locais  
  
-   Variáveis de tabela  
  
-   Tabelas retornadas nas funções com valor de tabela  
  
## <a name="internal-objects"></a>Objetos internos  
 Só há objetos internos em tempdb. Os seguintes objetos são incluídos nos contadores de páginas de objeto de usuário:  
  
-   Tabelas de trabalho para operações de cursor ou spool e armazenamento temporário de LOB (Objeto Grande)  
  
-   Arquivos de trabalho para operações, como junção de hash  
  
-   Execuções de classificação  
  
## <a name="relationship-cardinalities"></a>Cardinalidades de relações  
  
|De|Para|Relação|  
|----------|--------|------------------|  
|sys.dm_db_file_space_usage.database_id, file_id|sys.dm_io_virtual_file_stats.database_id, file_id|Um para um|  
  
## <a name="permissions"></a>Permissões

Em [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requer o `VIEW DATABASE STATE` no banco de dados.   

## <a name="examples"></a>Exemplos  
  
### <a name="determing-the-amount-of-free-space-in-tempdb"></a>Determinando a quantidade de espaço livre em tempdb  
 A consulta a seguir retorna o número total de páginas livres e o espaço livre total em megabytes (MB) disponível em todos os arquivos em **tempdb**.  
  
```sql
USE tempdb;  
GO  
SELECT SUM(unallocated_extent_page_count) AS [free pages],   
(SUM(unallocated_extent_page_count)*1.0/128) AS [free space in MB]  
FROM sys.dm_db_file_space_usage;  
```  

### <a name="determining-the-amount-of-space-used-by-user-objects"></a>Determinando o volume de espaço usado por objetos do usuário  
 A consulta a seguir retorna o número total de páginas usadas por objetos do usuário e o espaço total em MB usado por objetos internos em tempdb.  
  
```sql  
USE tempdb;  
GO  
SELECT SUM(user_object_reserved_page_count) AS [user object pages used],  
(SUM(user_object_reserved_page_count)*1.0/128) AS [user object space in MB]  
FROM sys.dm_db_file_space_usage;
```  
  
## <a name="see-also"></a>Consulte também  
 [Exibições e funções de gerenciamento dinâmico &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Banco de dados relacionados a exibições de gerenciamento dinâmico &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
