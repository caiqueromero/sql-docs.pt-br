---
title: dbo.sysproxies (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 82752574f0b3ef43d3f44967c14ef79a0779eae5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Define atributos de uma conta proxy do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Essa tabela é armazenada no **msdb** banco de dados.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**Int**|ID da conta proxy.|  
|**name**|**sysname**|Nome da conta proxy.|  
|**credential_id**|**Int**|ID da credencial que a conta proxy usa.|  
|**Habilitado**|**tinyint**|Status da conta proxy:<br /><br /> **0** = desabilitado. **1** = habilitado.|  
|**Descrição**|**nvarchar(512)**|Descrição que o usuário inseriu quando a conta proxy foi criada.|  
|**user_sid**|**varbinary(85)**|Microsoft Windows *security_identifier* do usuário ou grupo associado com a credencial de proxy.|  
|**credential_date_created**|**datetime**|Data e hora em que a credencial foi criada.|  
  
## <a name="remarks"></a>Remarks  
 Somente membros do **sysadmin** a função de servidor fixa pode acessar o **sysproxies** tabela.  
  
## <a name="see-also"></a>Consulte também  
 [dbo.sysproxylogin &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo.sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.syssubsystems &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
