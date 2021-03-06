---
title: Configurações (sincronização) (SybaseToSQL) do projeto | Microsoft Docs
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
ms.assetid: 2cd6bc01-b8e5-4312-83a4-eac66dc1d460
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2dd0db2f5767c6d9a41f7a2c920139e3e324e3c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-synchronization-sybasetosql"></a>Configurações de projeto (sincronização) (SybaseToSQL)
A página de sincronização do **configurações de projeto** caixa de diálogo contém configurações que personalizam como o SSMA carrega os objetos de banco de dados, como tabelas e procedimentos armazenados, em [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou do SQL Azure.  
  
Você pode acessar duas páginas diferentes de sincronização que contêm as mesmas configurações:  
  
-   Se você deseja especificar configurações para todos os projetos futuros do SSMA, no **ferramentas** menu, selecione **configurações de projeto padrão**, selecione o tipo de projeto de migração para o qual as configurações são necessárias para ser exibido ou alterado de **versão de destino de migração** lista suspensa e, em seguida, selecione **sincronização** na parte inferior do painel esquerdo.  
  
-   Para especificar as configurações para o projeto atual, no **ferramentas** menu, selecione **configurações de projeto**e, em seguida, selecione **sincronização** na parte inferior do painel esquerdo.  
  
## <a name="options"></a>Opções  
**Tentativas**  
Especifica o número de tentativas SSMA deve fazer ao carregar objetos em [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Objetos que não são carregados no [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] na tentativa atual será tentada novamente até que o SSMA atinge o número máximo de tentativas no processo de sincronização atual.  
  
## <a name="synchronization-for-sql-server"></a>Sincronização para o SQL Server  
**Atualizar o objeto local na alteração de objeto local e remoto**  
Especifica se o SSMA deve substituir os metadados do objeto local com metadados de objeto remoto se alterar objetos locais e remotos.  
Se você selecionar **de atualização do banco de dados**, SSMA carregar definições de banco de dados nos metadados quando a condição for atendida.  
Se você selecionar **gravar no banco de dados**, SSMA atualizará os objetos no banco de dados de acordo com o conteúdo de metadados do SSMA quando a condição for atendida.  
Se você selecionar **ignorar**, SSMA não executará qualquer ação de atualização.   
Conjunto de opção padrão é **gravar no banco de dados.**  
  
**Atualizar o objeto local na alteração de objeto local**  
Especifica se o SSMA deve substituir os metadados do objeto local com metadados de objeto remoto se o objeto remoto for alterado.  
Se você selecionar **de atualização do banco de dados**, SSMA carregar definições de banco de dados nos metadados quando a condição for atendida.  
Se você selecionar **gravar no banco de dados**, SSMA atualizará o objeto no banco de dados de acordo com o conteúdo de metadados do SSMA quando a condição for atendida.  
Se você selecionar **ignorar**, SSMA não executará qualquer ação de atualização.   
Conjunto de opção padrão é **gravar no banco de dados**.  
  
**Atualizar o objeto local na alteração do objeto remoto**  
Especifica se o SSMA deve substituir os metadados do objeto local com metadados de objeto remoto se o objeto remoto for alterado.  
Se você selecionar **de atualização do banco de dados**, SSMA carregar definições de banco de dados nos metadados quando a condição for atendida.  
Se você selecionar **gravar no banco de dados**, SSMA atualizará o objeto no banco de dados de acordo com o conteúdo de metadados do SSMA quando a condição for atendida.  
Se você selecionar **ignorar**, SSMA não executará qualquer ação de atualização.   
Conjunto de opção padrão é **de atualização do banco de dados**.  
  
**Atualização quando os metadados de objeto local estão ausente**  
Especifica se o SSMA deve criar metadados locais se existe um objeto no banco de dados de destino, mas não localmente.  
Se você selecionar **de atualização do banco de dados**, SSMA seleciona a atualização da opção de banco de dados quando a condição for atendida.  
Se você selecionar **gravar no banco de dados**, SSMA excluirá o objeto do banco de dados quando a condição for atendida.  
Se você selecionar **ignorar**, SSMA não executará qualquer ação de atualização.   
Conjunto de opção padrão é **de atualização do banco de dados**.  
  
