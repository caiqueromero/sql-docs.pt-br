---
title: sys.pdw_diag_sessions (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f9a5a3a19e840c37661b0db95fe5141824e267a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwdiagsessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contém informações sobre várias sessões de diagnósticas que foram criados no sistema.  
  
|Nome da coluna|Tipo de dados|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Nome da sessão de diagnóstico.<br /><br /> Chave para este modo de exibição.||  
|**xml_data**|**nvarchar(4000)**|Carga XML que descreve a sessão.||  
|**is_active**|**bit**|Sinalizador que indica se o sinalizador está ativo.||  
|**host_address**|**nvarchar(255)**|Endereço do computador que hospeda a definição de sessão (nó de controle).||  
|**principal_id**|**int**|ID do usuário que criou a sessão no nível do banco de dados.||  
|**database_id**|**int**|ID do banco de dados é o escopo da sessão de diagnóstico.|  
  
## <a name="see-also"></a>Consulte também  
 [SQL Data Warehouse e exibições de catálogo do Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  