---
title: Fazer backup de uma chave mestra de banco de dados | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: security
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ea45c037b4815c1009224b40cf1d0b2585f811cf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="back-up-a-database-master-key"></a>Fazer backup da chave mestra de um banco de dados
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Este tópico descreve como fazer o backup de uma chave mestra de banco de dados no [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] usando o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. A chave mestra de banco de dados é usada para criptografar outras chaves e certificados dentro de um banco de dados. Se ela for excluída ou estiver corrompida, é possível que o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não consiga descriptografar essas chaves e os dados criptografados com elas poderão ser efetivamente perdidos. Por esta razão, faça backup da chave mestra de banco de dados e armazene o backup em um local externo seguro.  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Limitações e restrições](#Restrictions)  
  
     [Segurança](#Security)  
  
-   [Para fazer o backup de uma chave mestra de banco de dados usando o Transact-SQL](#Procedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Restrictions"></a> Limitações e restrições  
  
-   A chave mestra deve estar aberta e, portanto, descriptografada antes de ser feito o back up. Se for criptografada com a chave mestra de serviço, a chave mestra não terá que ser aberta explicitamente. No entanto, se a chave mestra só for criptografada com uma senha, ela deve ser aberta explicitamente.  
  
-   Recomendamos que você faça o backup da chave mestra assim que ela for criada e armazene o backup em um local externo seguro.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Exige a permissão CONTROL no banco de dados.  
  
##  <a name="Procedure"></a> Usando o SQL Server Management Studio com o Transact-SQL  
  
#### <a name="to-back-up-the-database-master-key"></a>Fazer backup da chave mestra de banco de dados  
  
1.  No [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], conecte à instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que contém a chave mestra do banco de dados da qual você deseja fazer backup.  
  
2.  Escolha uma senha que será usada para criptografar a chave mestra de banco de dados na mídia de backup. Esta senha está sujeita à verificação de complexidade.  
  
3.  Obtenha uma mídia de backup removível para armazenar uma cópia da chave de backup.  
  
4.  Identifique um diretório NTFS no qual criar o backup da chave. É aí que você criará o arquivo especificado na próxima etapa. O diretório deve ser protegido com ACLs (listas de controle de acesso) altamente restritivas.  
  
5.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
6.  Na barra Padrão, clique em **Nova Consulta**.  
  
7.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  O caminho do arquivo para a chave e a senha da chave (se existir) serão diferentes do que é indicado acima. Certifique-se de que ambos sejam específicos da sua configuração de servidor e chave.  
  
8.  Copie o arquivo na mídia de backup e verifique a cópia.  
  
9. Armazene o backup em um local seguro, fora do site.  
  
 Para obter mais informações, veja [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md) e [BACKUP MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md).  
  
  
