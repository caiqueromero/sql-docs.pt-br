---
title: Tarefas específicas de programação | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SQL Server Management Objects, tasks
- SMO [SQL Server], programming
- SMO [SQL Server], tasks
ms.assetid: a15949ef-88d9-4205-892e-0b66588b4fcc
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6878e0e429bf826d4dc3f6b57f8df42645f22dd5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="programming-specific-tasks"></a>Tarefas específicas de programação
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  As tarefas específicas de programação que usam objetos SMO incluem assuntos complexos que apenas serão exigidos por programas com uma função específica, como backup, monitoramento de estatísticas, replicação, gerenciamento de objetos de instância e definição de opções de configuração.  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Usando servidores vinculados no SMO](../../../relational-databases/server-management-objects-smo/tasks/using-linked-servers-in-smo.md)|Descreve como o SMO usa o objeto <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> para vincular servidores OLE-DB.|  
|[Configurando o SQL Server no SMO](../../../relational-databases/server-management-objects-smo/tasks/configuring-sql-server-in-smo.md)|Descreve como exibir e modificar definições de configuração para a instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] no SMO.|  
|[Usando o particionamento de tabela e índice](../../../relational-databases/server-management-objects-smo/tasks/using-table-and-index-partitioning.md)|Descreve como usar o particionamento de índice e tabela no SMO.|  
|[Usando grupos de arquivos e arquivos para armazenar dados](../../../relational-databases/server-management-objects-smo/tasks/using-filegroups-and-files-to-store-data.md)|Descreve como usar grupos de arquivos no SMO.|  
|[Gerenciando serviços e configurações de rede através do provedor do WMI](../../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)|Descreve vários modos de acompanhar a instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usando o objeto <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> que representa o Provedor WMI para Gerenciamento de Configuração.|  
|[Trabalhando com objetos de banco de dados](../../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-database-objects.md)|Descreve como criar classes de instância que representam objetos na instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Gerenciando usuários, funções e logons](../../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)|Descreve como usar funções de segurança no SMO.|  
|[Concedendo, revogando e negando permissões](../../../relational-databases/server-management-objects-smo/tasks/granting-revoking-and-denying-permissions.md)|Descreve como usar o SMO para conceder, revogar e negar permissões a usuários ou membros de uma função.|  
|[Usando a criptografia](../../../relational-databases/server-management-objects-smo/tasks/using-encryption.md)|Descreve como proteger dados que usam criptografia no SMO.|  
|[Agendando tarefas administrativas automáticas no SQL Server Agent](../../../relational-databases/server-management-objects-smo/tasks/scheduling-automatic-administrative-tasks-in-sql-server-agent.md)|Descreve como usar o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent para monitorar, relatar e agendar trabalhos no SMO.|  
|[Fazendo backup e restaurando bancos de dados e logs de transações](../../../relational-databases/server-management-objects-smo/tasks/backing-up-and-restoring-databases-and-transaction-logs.md)|Descreve como fazer backup e restaurar bancos de dados e logs de transações no SMO.|  
|[Script](../../../relational-databases/server-management-objects-smo/tasks/scripting.md)|Descreve como criar script de objetos e descobrir dependências entre objetos no SMO.|  
|[Transferindo dados](../../../relational-databases/server-management-objects-smo/tasks/transferring-data.md)|Descreve como transferir dados no SMO.|  
|[Usando o Database Mail](../../../relational-databases/server-management-objects-smo/tasks/using-database-mail.md)|Descreve como o SMO utiliza serviços de e-mail.|  
|[Gerenciando o Service Broker](../../../relational-databases/server-management-objects-smo/tasks/managing-service-broker.md)|Descreve como configurar o Service Broker usando o SMO.|  
|[Usando esquemas XML](../../../relational-databases/server-management-objects-smo/tasks/using-xml-schemas.md)|Descreve como usar o tipo de dados XML no SMO.|  
|[Usando sinônimos](../../../relational-databases/server-management-objects-smo/tasks/using-synonyms.md)|Descreve como criar sinônimos no SMO.|  
|[Usando mensagens](../../../relational-databases/server-management-objects-smo/tasks/using-messages.md)|Descreve como usar mensagens de sistema e como definir suas próprias mensagens definidas pelo usuário.|  
|[Implementando a pesquisa de texto completo](../../../relational-databases/server-management-objects-smo/tasks/implementing-full-text-search.md)|Descreve como implementar catálogos de pesquisa de texto completo e índices no SMO.|  
|[Implementando pontos de extremidade](../../../relational-databases/server-management-objects-smo/tasks/implementing-endpoints.md)|Descreve como criar pontos de extremidade para controlar as cargas de Monitoramento de Banco de Dados, de solicitações de protocolo SOAP e de Service Broker.|  
|[Criando e atualizando estatísticas](../../../relational-databases/server-management-objects-smo/tasks/creating-and-updating-statistics.md)|Descreve como configurar e monitorar estatísticas em um banco de dados no SMO.|  
|[Rastreando e reproduzindo eventos](../../../relational-databases/server-management-objects-smo/tasks/tracing-and-replaying-events.md)|Descreve como usar o **rastreamento** e **repetir** objetos no SMO para eventos de rastreamento e reprodução.|  
  
  
