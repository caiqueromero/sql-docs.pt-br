---
title: 'Etapa 3: adicionar e configurar um gerenciador de conexões OLE DB | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3fcaef3b8520db8c595449b28f0906399b9265ce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-1-3---adding-and-configuring-an-ole-db-connection-manager"></a>Lição 1-3 – adicionar e configurar um gerenciador de conexões OLE DB
Depois de ter adicionado um gerenciador de conexões de arquivo simples para conectar-se à origem de dados, a próxima tarefa é adicionar um gerenciador de conexões OLE DB para conectar-se ao destino. Um gerenciador de conexões OLE DB permite que um pacote extraia dados de qualquer fonte de dados compatível com OLE DB ou carregue dados nela. Usando o gerenciador de conexões OLE DB, você pode especificar o servidor, o método de autenticação e o banco de dados padrão para a conexão.  
  
Nesta lição, você aprenderá a criar um gerenciador de conexões OLE DB que usa a Autenticação do Windows para se conectar à instância local do **AdventureWorksDB2012**. O gerenciador de conexões OLE DB que você criar também será referenciado por outros componentes que você criar posteriormente neste tutorial, como, por exemplo, a transformação Pesquisa e o destino OLE DB.  
  
### <a name="add-and-configure-an-ole-db-connection-manager-to-the-ssis-package"></a>Adicionar e configurar um Gerenciador de Conexões OLE DB no pacote SSIS  
  
1.  Clique com o botão direito do mouse em qualquer lugar da área **Gerenciadores de Conexões** e clique em **Nova Conexão OLE DB**.  
  
2.  Na caixa de diálogo **Configurar Gerenciador de Conexões OLE DB** , clique em **Novo**.  
  
3.  Em **Nome do servidor**, insira **localhost**.  
  
    Quando você especifica localhost como o nome do servidor, o gerenciador de conexões se conecta à instância padrão do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] no computador local. Para usar uma instância remota do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], substitua localhost pelo nome do servidor ao qual você deseja se conectar.  
  
4.  No grupo **Fazer logon no servidor** , verifique se a opção **Usar Autenticação do Windows** está selecionada.  
  
5.  No grupo **Conectar-se a um banco de dados** , na caixa **Selecionar ou inserir um nome de banco de dados** , digite ou selecione **AdventureWorksDW2012**.  
  
6.  Clique em **Testar Conexão** para verificar se as configurações de conexão especificadas são válidas.  
  
7.  Clique em **OK**.  
  
8.  Clique em **OK**.  
  
9. No painel **Conexões de Dados** da caixa de diálogo **Configurar Gerenciador de Conexões OLE DB** , verifique se a opção **localhost.AdventureWorksDW2012** está selecionada.  
  
10. Clique em **OK**.  
  
## <a name="next-task-in-lesson"></a>Próxima tarefa da lição  
[Etapa 4: Adicionando uma tarefa de fluxo de dados ao pacote](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a>Consulte Também  
[Gerenciador de conexões OLE DB](../integration-services/connection-manager/ole-db-connection-manager.md)  
  
