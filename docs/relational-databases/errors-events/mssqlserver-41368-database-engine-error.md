---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
robots: noindex,nofollow
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9161b32ff6c9c2e2ee03b5909ee69db1594bbd9d
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID do evento|41368|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|Texto da mensagem|Há suporte para o acesso às tabelas com otimização de memória usando o nível de isolamento READ COMMITTED somente em transações de confirmação automática. Ele não tem suporte para transações implícitas ou explícitas. Forneça um nível de isolamento com suporte para a tabela com otimização de memória usando uma dica de tabela, como WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Explicação  
O acesso às tabelas com otimização de memória usando o nível de isolamento READ COMMITTED tem suporte somente para transações de confirmação automática. Para obter mais informações, consulte [Transações com tabelas e procedimentos na memória](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md).  
  
Ao acessar uma tabela com otimização de memória de uma transação explícita que é iniciada com BEGIN TRANSACTION, ou de uma transação implícita, se IMPLICIT_TRANSACTIONS estiver definido como ON, o nível de isolamento READ COMMITTED não terá suporte.  
  
## <a name="user-action"></a>Ação do usuário  
Ao acessar uma tabela com otimização de memória de uma transação READ COMMITTED explícita ou implícita, use SNAPSHOT para acessar a tabela. Isso pode ser obtido usando a dica de tabela WITH (SNAPSHOT) (para obter mais informações, consulte [Transações com tabelas e procedimentos na memória](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)) ou definindo a opção de banco de dados MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT como ON (para obter mais informações, consulte [Opções ALTER DATABASE SET &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql.md)).  
  
## <a name="see-also"></a>Consulte também  
[OLTP na memória &#40;Otimização na memória&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
