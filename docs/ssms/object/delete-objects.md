---
title: Excluir objetos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: debf80be51388ab413d2ca7c08f189e03b9154e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="delete-objects"></a>Excluir Objetos
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Use essa caixa de diálogo para excluir um banco de dados ou objeto de banco de dados.  
  
## <a name="uielement-list"></a>Lista de elementos de interface do usuário  
**Objeto a ser excluído**  
Exibe os nomes, os tipos, os proprietários e o status dos objetos a serem excluídos, bem como qualquer mensagem sobre erros durante a execução.  
  
> [!NOTE]  
> Executar **Excluir** em um banco de dados é equivalente a emitir DROP DATABASE em [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Mostrar Dependências**  
Clique para exibir os objetos que são dependentes do objeto selecionado atualmente e os objetos dos quais o objeto selecionado é dependente (dependência ascendente e descendente). As informações exibidas na caixa de diálogo **Mostrar Dependências** são somente leitura.  
  
> [!NOTE]  
> O botão **Mostra Dependências** não aparece para todos os tipos de objetos de banco de dados. Para exibir as dependências quando o botão **Mostrar Dependências** não está disponível, clique com o botão direito do mouse no Pesquisador de Objetos e em **Exibir Dependências**.  
  
**Exclua informações de backup e de histórico de restauração para os bancos de dados**  
Aparece somente quando um banco de dados é excluído, essa caixa de seleção faz com que o backup e o histórico de restauração do banco de dados de assunto sejam excluídos do banco de dados **msdb** .  
  
**Encerre as conexões existentes**  
Aparece somente quando um banco de dados é excluído, essa caixa de seleção encerra as conexões com o banco de dados de assunto.  
  
