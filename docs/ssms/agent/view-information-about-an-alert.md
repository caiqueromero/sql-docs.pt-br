---
title: "Exibir informações sobre um alerta | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5bfe05dde95b8fdb47893ea17802b0798de9762a
ms.lasthandoff: 04/11/2017

---
# <a name="view-information-about-an-alert"></a>Exibir informações sobre um alerta
Este tópico descreve como exibir infoumações sobre alertas do [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent no [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Neste tópico**  
  
-   **Antes de começar:**  
  
    [Segurança](#Security)  
  
-   **Para exibir informações sobre um alerta, usando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Antes de começar  
  
### <a name="Security"></a>Segurança  
  
#### <a name="Permissions"></a>Permissões  
Por padrão, os membros da função de servidor fixa **sysadmin** podem exibir as informações sobre um alerta. Deve ser concedida a outros usuários a função de banco de dados fixa **SQLAgentOperatorRole** no banco de dados **msdb** .  
  
## <a name="SSMSProcedure"></a>Usando o SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-alert"></a>Para exibir informações sobre um alerta  
  
1.  No **Pesquisador de Objetos** , clique no sinal de adição para expandir o servidor no qual você deseja exibir informações sobre um alerta.  
  
2.  Clique no sinal de adição para expandir o **SQL Server Agent**.  
  
3.  Clique no sinal de adição para expandir a pasta **Alertas** .  
  
4.  Clique com o botão direito do mouse no alerta que tem as informações que você deseja exibir e selecione **Propriedades**.  
  
    Para obter mais informações sobre as opções disponíveis contidas na caixa de diálogo *alert_name***propriedades do alerta** , consulte:  
  
    -   [Propriedades do alerta – Novo alerta &amp;#40;página Geral&amp;#41;](../../ssms/agent/alert-properties-new-alert-general-page.md)  
  
    -   [Propriedades do alerta – Novo alerta &amp;#40;página Resposta&amp;#41;](../../ssms/agent/alert-properties-new-alert-response-page.md)  
  
    -   [Propriedades do alerta – Novo alerta &amp;#40;página Opções&amp;#41;](../../ssms/agent/alert-properties-new-alert-options-page.md)  
  
    -   [Propriedades do alerta &amp;#40;página Histórico&amp;#41;](../../ssms/agent/alert-properties-history-page.md)  
  
5.  Quando terminar, clique em **OK**.  
  
## <a name="TsqlProcedure"></a>Usando Transact-SQL  
  
#### <a name="to-view-information-about-an-alert"></a>Para exibir informações sobre um alerta  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
Para obter mais informações, veja [sp_help_alert (Transact-SQL)](http://msdn.microsoft.com/en-us/850cef4e-6348-4439-8e79-fd1bca712091).  
  
