---
title: sysconfigures (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
caps.latest.revision: 39
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 45b1fc8a1db24d767ef394cb4b3c1b1cda1304b7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contém uma linha para cada opção de configuração definida por um usuário. **sysconfigures** contém as opções de configuração que são definidas antes da inicialização mais recente do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], além de opções de configuração dinâmica definida desde então.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**value**|**Int**|Valor modificável pelo usuário para a variável. Isso só será usado pelo [!INCLUDE[ssDE](../../includes/ssde-md.md)] se RECONFIGURE tiver sido executado.|  
|**config**|**Int**|Número variável de configuração.|  
|**comment**|**nvarchar(255)**|Explicação da opção de configuração.|  
|**status**|**smallint**|Bitmap que indica o status da opção. Os possíveis valores incluem os seguintes:<br /><br /> 0 = Estático. A definição entra em vigor quando o servidor é reinicializado.<br /><br /> 1 = Dinâmico. A variável é implementada quando a instrução RECONFIGURE é executada.<br /><br /> 2 = Avançado. Variável é exibida somente quando o **Mostrar opções avançadas** está definido. A definição entra em vigor quando o servidor é reinicializado.<br /><br /> 3 = Dinâmico e avançado.|  
  
## <a name="see-also"></a>Consulte também  
 [Mapeando tabelas do sistema para exibições do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Exibições de compatibilidade &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
