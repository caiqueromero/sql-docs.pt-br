---
title: Conecte-se ao banco de dados do SQL Azure (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: f73b6e88e457ef74a82512876715a333d0a52d71
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Conecte-se ao banco de dados do SQL Azure (SybaseToSQL)
Use a conectar-se a caixa de diálogo banco de dados do Azure SQL para se conectar ao banco de dados Azure SQL DB que você deseja migrar.  
  
Para acessar essa caixa de diálogo, no **arquivo** menu, selecione **conectar-se ao banco de dados do Azure SQL**. Se você se conectou anteriormente, o comando é **reconectar-se ao banco de dados de SQL do Azure.**  
  
## <a name="options"></a>Opções  
**Nome do servidor**  
  
Selecione ou insira o nome do servidor para se conectar ao banco de dados de SQL do Azure.  
  
**Banco de dados**  
  
Selecione, digite ou **procurar** o nome do banco de dados.  
  
> [!IMPORTANT]  
> SSMA para Sybase não oferece suporte a conexão ao banco de dados mestre no banco de dados de SQL do Azure.  
  
**Nome de usuário**  
  
Insira o nome de usuário SSMA usará para se conectar ao banco de dados do banco de dados de SQL do Azure  
  
**Senha**  
  
Digite a senha para o nome de usuário.  
  
**Encrypt**  
  
O SSMA recomenda conexão criptografada para o banco de dados do Azure SQL.  
  
## <a name="create-azure-database"></a>Criar banco de dados do Azure  
Se não houver nenhum banco de dados na conta de banco de dados de SQL do Azure, você pode criar o primeiro banco de dados.  
  
Para criar um novo banco de dados pela primeira vez, siga as etapas a seguir  
  
1.  Clique no botão Procurar que está presente em conectar-se a caixa de diálogo banco de dados de SQL do Azure  
  
2.  Se não houver nenhum banco de dados, os seguintes itens de dois menu aparecem.  
  
    1.  **(nenhum banco de dados encontrado)**  que é desabilitado ou esmaecido sempre  
  
    2.  **Criar novo banco de dados** que é habilitado apenas quando não há nenhum banco de dados na conta de banco de dados de SQL do Azure. Ao clicar neste item de menu, caixa de diálogo Criar banco de dados do Azure está presente com o nome do banco de dados e tamanho.  
  
3.  No momento da criação do banco de dados, os dois parâmetros a seguir recebem como entrada:  
  
    1.  **Nome do banco de dados:** digite o nome do banco de dados.  
  
    2.  **Tamanho do banco de dados:** selecione o tamanho do banco de dados que você precisa criar conta de banco de dados de SQL do Azure.  
  
