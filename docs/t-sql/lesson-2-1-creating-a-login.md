---
title: Criando um logon | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- creating a login
ms.assetid: a2512310-bdb6-41dc-858a-e866b2b58afc
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 32fc25ba0eca6fa991f4bdccdea393d19685839c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-2-1---creating-a-login"></a>Lição 2-1: criando um logon
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Para acessar o [!INCLUDE[ssDE](../includes/ssde-md.md)], os usuários precisam de um logon. O logon pode representar a identidade do usuário como conta do Windows ou como membro de um grupo do Windows, ou o logon pode ser um logon do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que exista apenas no [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Sempre que possível, você deverá usar a Autenticação do Windows.  
  
Por padrão, os administradores têm acesso completo ao [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]no seu computador. Nesta lição, pretendemos ter um usuário menos privilegiado. Dessa forma, você criará uma nova conta local de Autenticação do Windows em seu computador. Para fazer isso, você precisa ser administrador do computador. E conceder acesso ao [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ao novo usuário.  
  
### <a name="to-create-a-new-windows-account"></a>Para criar uma nova conta do Windows  
  
1.  Clique em **Iniciar**, em **Executar**, na caixa **Abrir** , digite **%SystemRoot%\system32\compmgmt.msc /s**e clique em **OK** para abrir o programa de Gerenciamento do Computador.  
  
2.  Em **Ferramentas do Sistema**, expanda **Usuários e Grupos Locais**, clique com o botão direito do mouse em **Usuários**e clique em **Novo Usuário**.  
  
3.  Na caixa **Nome de usuário** digite **Mary**.  
  
4.  Na caixa **Senha** e **Confirmar senha** , digite uma senha forte e clique em **Criar** para gerar um novo usuário local do Windows.  
  
### <a name="to-create-a-login"></a>Para criar um logon  
  
1.  Em uma janela do Editor de Consulta do [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], digite e execute o código a seguir substituindo `computer_name` pelo nome de seu computador. `FROM WINDOWS` indica que o Windows autenticará o usuário. O argumento opcional `DEFAULT_DATABASE` é conectado `Mary` ao banco de dados `TestData` , a menos que a cadeia de caracteres de conexão indique outro banco de dados. Essa instrução introduz o ponto-e-vírgula como término opcional para uma instrução [!INCLUDE[tsql](../includes/tsql-md.md)] .  
  
    ```  
    CREATE LOGIN [computer_name\Mary]  
        FROM WINDOWS  
        WITH DEFAULT_DATABASE = [TestData];  
    GO  
    ```  
  
    Isso autoriza o nome de usuário `Mary`, autenticado pelo seu computador, a acessar a instância do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Se houver mais de uma instância do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] no computador, você deverá criar o logon em cada instância que `Mary` deve acessar.  
  
    > [!NOTE]  
    > Como `Mary` não é uma conta de domínio, esse nome de usuário só poderá ser autenticado nesse computador.  
  
## <a name="next-task-in-lesson"></a>Próxima tarefa da lição  
[concedendo acesso a um banco de dados](../t-sql/lesson-2-2-granting-access-to-a-database.md)  
  
## <a name="see-also"></a>Consulte Também  
[CREATE LOGIN &#40;Transact-SQL&#41;](../t-sql/statements/create-login-transact-sql.md)  
[Escolher um modo de autenticação](../relational-databases/security/choose-an-authentication-mode.md)  
  
  
  
