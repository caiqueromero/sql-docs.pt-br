---
title: Localizar um nó específico em uma rede de dependência | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ad00f715533e5da24cbec9c61dc79a045fa035ef
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="find-a-specific-node-in-a-dependency-network"></a>Localizar um nó específico em uma rede de dependência
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Uma rede de dependência em um modelo de mineração do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pode conter muitos nós, dificultando a localização dos dados de seu interesse. Para resolver esse problema, você pode usar a caixa de diálogo **Localizar Nó** na guia **Rede de Dependências** do Designer de Mineração de Dados para procurar um nó específico.  
  
### <a name="to-find-a-specific-node-in-a-dependency-network"></a>Para localizar um nó específico em uma rede de dependências  
  
1.  Na guia **Visualizador do Modelo de Mineração** do **Designer de Mineração de Dados** no [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], clique em **Localizar Nó** na barra de ferramentas da guia **Rede de Dependências** do visualizador do modelo de mineração.  
  
     A caixa de diálogo **Localizar Nó** é exibida.  
  
2.  Na caixa **O nome do nó contém** , insira parte do nome do nó que você deseja pesquisar.  
  
     A lista de nós é filtrada para exibir só os nós que contêm parte do caminho de pesquisa.  
  
3.  Selecione o nó correto da lista e clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas do Visualizador do modelo e instruções de mineração](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
