---
title: Desabilitar restrições Foreign Key com instruções INSERT e UPDATE | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
- UPDATE statement [SQL Server], foreign key constraints
- INSERT statement [SQL Server], foreign key constraints
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f516accaa507a1bb4f1bcce42e42f20c21a85fc3
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="disable-foreign-key-constraints-with-insert-and-update-statements"></a>Desabilitar restrições FOREIGN KEY com instruções INSERT e UPDATE
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Você pode desabilitar uma restrição de chave estrangeira durante transações INSERT e UPDATE no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Use essa opção se você souber que novos dados não violarão a restrição existente ou se a restrição se aplicar somente aos dados que já estão no banco de dados.  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Limitações e restrições](#Restrictions)  
  
     [Segurança](#Security)  
  
-   **Para desabilitar uma restrição de chave estrangeira para instruções INSERT e UPDATE usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Restrictions"></a> Limitações e restrições  
 Depois de desabilitar essas restrições, as inserções ou atualizações futuras na coluna não serão validadas em relação às condições de restrição.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Exige a permissão ALTER na tabela.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a>Para desabilitar uma restrição de chave estrangeira para instruções INSERT e UPDATE  
  
1.  No **Pesquisador de Objetos**, expanda a tabela com a restrição e expanda a pasta **Chaves** .  
  
2.  Clique com o botão direito do mouse na restrição e selecione **Modificar**.  
  
3.  Na grade em **Designer de Tabela**, clique em **Impor Restrição de Chave Estrangeira** e selecione **Não** no menu suspenso.  
  
4.  Clique em **Fechar**.  
  
##  <a name="TsqlProcedure"></a> Usando o Transact-SQL  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a>Para desabilitar uma restrição de chave estrangeira para instruções INSERT e UPDATE  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole os exemplos a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 Para obter mais informações, veja [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
