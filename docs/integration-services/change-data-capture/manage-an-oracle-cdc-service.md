---
title: Gerenciar um serviço Oracle CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: change-data-capture
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 64c1702e49bf68edd9e5b3abf316ea9289d9a6ce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="manage-an-oracle-cdc-service"></a>Manage an Oracle CDC Service
  Você pode usar o Console de Configuração do Serviço CDC para gerenciar um Serviço CDC específico.  
  
 **Para selecionar o serviço CDC com o qual você deseja trabalhar**  
  
1.  No painel esquerdo no Console de Configuração do Serviço CDC, expanda **Serviços Locais de CDC**.  
  
2.  Selecione o serviço CDC com o qual você deseja trabalhar.  
  
     Você também pode clicar com o botão direito no serviço CDC com o qual você deseja trabalhar e selecionar a ação desejada. Consulte [O que pode fazer você com um Serviço ](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
 **OR**  
  
1.  Selecione **Serviços Locais de CDC** no painel esquerdo no Console de Configuração do Serviço de CDC.  
  
2.  Da seção do meio do Console de Configuração do Serviço CDC, selecione o serviço com o qual você deseja trabalhar.  
  
     Você também pode clicar com o botão direito no serviço CDC com o qual você deseja trabalhar e selecionar a ação desejada. Consulte [O que pode fazer você com um Serviço ](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
##  <a name="BKMK_WhatcandowithCDCService"></a> O que pode fazer você com um Serviço CDC  
 Você pode realizar as seguintes ações ao trabalhar com um serviço CDC.  
  
### <a name="delete-the-service"></a>Excluir o serviço  
 No painel **Ações** no lado direito do Console de Configuração do Serviço CDC, clique em **Excluir** para excluir o serviço.  
  
 Você também pode clicar com o botão direito do mouse no serviço CDC que deseja excluir e selecionar **Excluir**.  
  
 **Observação**: se o serviço estiver sendo executado ao excluir o serviço, ele será parado antes de ser excluído.  
  
 Para excluir a definição de Serviço do Windows do Oracle CDC, o programa precisa de acesso de atualização ao banco de dados MSXDBCDC na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associada. Quando você clicar em OK para excluir o serviço, o programa tentará excluir o registro do Serviço Oracle CDC no banco de dados MSXDBCDC. Se o programa não puder excluir o registro do Serviço Oracle CDC porque não tem as permissões corretas, ele solicitará que o usuário insira um logon do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com permissões de atualização para o banco de dados MSXDBCDC.  
  
 Para obter informações sobre os dados que você deverá inserir na caixa de diálogo Conecte-se ao SQL Server, consulte [Connection to SQL Server for Delete](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md).  
  
### <a name="edit-the-cdc-service-properties"></a>Editar as propriedades de serviço CDC  
 No painel **Ações** no lado direito do Console de Configuração do Serviço CDC, clique em **Propriedades**.  
  
 Você também pode clicar com o botão direito do mouse no serviço CDC em que deseja editar as propriedades e selecionar **Propriedades**.  
  
## <a name="see-also"></a>Consulte Também  
 [Como gerenciar um serviço CDC local](../../integration-services/change-data-capture/how-to-manage-a-local-cdc-service.md)  
  
  
