---
title: Opções (página Ambiente – Geral) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-menu
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.TOOLSOPTIONSPAGES.ENVIRONMENT.GENERAL
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
- DevLang-TSQL
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f7e8ba6dcb66fbf962e70cc5175b07095ffa2f5d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="options-environment---general-page"></a>Opções (Ambiente – página Geral)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Use a caixa de diálogo **Opções** para configurar ações de inicialização do [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], opções gerais de gerenciamento de janelas e outras configurações gerais. No menu **Ferramentas** , clique em **Opções**, expanda a pasta **Ambiente** e clique em **Geral**.  
  
## <a name="uielement-list"></a>Lista de elementos de interface do usuário  
**Na inicialização**  
Selecione a ação a ser executada pelo [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] quando for iniciado. As opções são:  
  
-   **Abrir Pesquisador de Objetos** solicita uma conexão e abre o Pesquisador de Objetos.  
  
-   **Abrir nova janela de consulta** solicita uma conexão e abre o Editor de Consultas SQL.  
  
-   **Abrir Pesquisador de Objetos e nova consulta** solicita uma conexão e, depois, abre o Pesquisador de Objetos e o Editor de Consultas SQL com essa conexão.  
  
-   **Abrir ambiente vazio** abre o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] sem uma janela do Editor de Consultas SQL e sem conectar o Pesquisador de Objetos com um servidor.  
  
**Ocultar objetos do sistema no Pesquisador de Objetos**  
Marque essa caixa de seleção para remover os bancos de dados, tabelas e exibições do sistema e os procedimentos armazenados do sistema da exibição em árvore no Pesquisador de Objetos. As funções e tipos de dados do sistema não são ocultos. Essa opção só se aplica a instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e não afeta servidores já conectados no Pesquisador de Objetos.  
  
## <a name="environment-layout"></a>Layout do Ambiente  
Você deve fechar e reabrir o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] para alternar entre os modos de ambiente de documentos com guias e de ambiente MDI.  
  
**Documentos com guias**  
Selecione esta opção para exibir janelas de documentos com guias em editores. Janelas de documentos com guias são úteis para organizar e alternar entre vários documentos abertos.  
  
**Ambiente MDI**  
Selecione esta opção para abrir documentos em um ambiente MDI. Janelas de documentos MDI são úteis para garantir o espaço na tela que, de outra forma, seria ocupado pelas guias no ambiente de documentos com guias. Ao trabalhar no modo MDI, você pode alternar entre os documentos pressionando CTRL+TAB ou usar as opções lado a lado localizadas no menu **Janela** .  
  
## <a name="docked-tool-window-behavior"></a>Comportamento da Janela de Ferramentas Encaixada  
**O botão Fechar afeta somente a guia ativa**  
Especifica que, quando essa caixa de seleção for marcada, somente a janela de ferramentas exibida no momento será fechada e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, esta caixa é selecionada.  
  
**O botão Ocultar Automaticamente afeta somente a guia ativa**  
Especifica que, quando essa caixa de seleção for marcada, somente a janela de ferramentas exibida no momento será oculta automaticamente e não todas as janelas de ferramentas do conjunto encaixado. Por padrão, essa caixa de seleção é desmarcada.  
  
## <a name="display"></a>Exibição  
**Exibir n arquivos na lista dos usados recentemente**  
Personaliza o número de projetos e arquivos recentes exibidos no menu **Arquivo** . Digite um número entre 1 e 24. O padrão é 4. Esse é um modo fácil de recuperar projetos de script e projetos de arquivos e script recentemente usados.  
  
