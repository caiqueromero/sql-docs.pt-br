---
title: sp_changemergefilter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changemergefilter_TSQL
- sp_changemergefilter
helpviewer_keywords:
- sp_changemergefilter
ms.assetid: e08fdfdd-d242-4e85-817b-9f7a224fe567
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 332cb7bd6d4afa477064bd014e36dc2e5b6e8aa7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="spchangemergefilter-transact-sql"></a>sp_changemergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Altera algumas propriedades do filtro de mesclagem. Esse procedimento armazenado é executado no Publicador, no banco de dados publicador.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_changemergefilter [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
        , [ @filtername= ] 'filtername'  
        , [ @property= ] 'property'  
        , [ @value= ] 'value'  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication=** ] **'***publicação***'**  
 É o nome da publicação. *publicação* é **sysname**, sem padrão.  
  
 [  **@article=** ] **'***artigo***'**  
 É o nome do artigo. *artigo* é **sysname**, sem padrão.  
  
 [  **@filtername=** ] **'***filtername***'**  
 É o nome atual do filtro. *FilterName* é **sysname**, sem padrão.  
  
 [  **@property=** ] **'***propriedade***'**  
 É o nome da propriedade a ser alterada. *propriedade* é **sysname**, sem padrão.  
  
 [  **@value=**] **'***valor***'**  
 É o novo valor da propriedade especificada. *valor*é **nvarchar (1000)**, sem padrão.  
  
 Essa tabela descreve as propriedades de artigos e os valores dessas propriedades.  
  
|Propriedade|Value|Description|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|Filtro de junção.<br /><br /> Essa opção é requerida para suporte a Assinantes [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
||**2**|Relação de registro lógico.|  
||**3**|Filtro de junção é também uma relação de registro lógico.|  
|**FilterName**||Nome do filtro.|  
|**join_articlename**||Nome do artigo de junção.|  
|**join_filterclause**||Cláusula de filtro.|  
|**join_unique_key**|**true**|A junção está em uma chave exclusiva|  
||**false**|A junção não está em uma chave exclusiva.|  
  
 [  **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 Confirma que a ação tomada por esse procedimento armazenado pode invalidar um instantâneo existente. *force_invalidate_snapshot* é um **bit**, com um padrão **0**.  
  
 **0** Especifica que as alterações no artigo de mesclagem fazem com que o instantâneo seja inválido. Se o procedimento armazenado detectar que a alteração requer um novo instantâneo, ocorrerá um erro e nenhuma alteração será feita.  
  
 **1** significa que as alterações no artigo de mesclagem podem invalidar o instantâneo inválido, e se houver assinaturas existentes que exigem um novo instantâneo, dará permissão para o instantâneo existente seja marcado como obsoleto e um novo instantâneo seja gerado.  
  
 [  **@force_reinit_subscription =** ] *force_reinit_subscription*  
 Confirma que a ação tomada por esse procedimento armazenado pode exigir que as assinaturas existentes sejam reinicializadas. *force_reinit_subscription* é um **bit** com um padrão de **0**.  
  
 **0** Especifica que as alterações no artigo de mesclagem fazem com que a assinatura ser reiniciada. Se o procedimento armazenado detectar que a alteração irá requerer assinaturas existentes para ser reiniciada, ocorrerá um erro e nenhuma alteração será feita.  
  
 **1** significa que as alterações no artigo de mesclagem fará com que as assinaturas existentes sejam reinicializadas e dá permissão para que ocorra a reinicialização da assinatura.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Remarks  
 **sp_changemergefilter** é usado em replicação de mesclagem.  
  
 A alteração do filtro em um artigo de mesclagem requer que o instantâneo, se existir, seja recriado. Isso é feito definindo o **@force_invalidate_snapshot** para **1**. Além disso, se houver assinaturas para este artigo, elas deverão ser reiniciadas. Isso é feito definindo o **@force_reinit_subscription** para **1**.  
  
 Para usar registros lógicos, a publicação e os artigos devem atender a vários requisitos. Para obter mais informações, consulte [Agrupar alterações a linhas relacionadas com registros lógicos](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **sysadmin** função de servidor fixa ou **db_owner** pode executar a função de banco de dados fixa **sp_changemergefilter**.  
  
## <a name="see-also"></a>Consulte também  
 [Alterar propriedades da publicação e do artigo](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
