---
title: Visão geral do Assistente de migração de dados (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, overview
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: dd681a6445c6759b0ec17e06dc0b4dbf24b3b72f
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707964"
---
# <a name="overview-of-data-migration-assistant"></a>Visão geral do Assistente de migração de dados

O Assistente de migração do dados (DMA) permite que você faça a atualização para uma plataforma de dados modernos detectando problemas de compatibilidade que podem afetar a funcionalidade de banco de dados em sua nova versão do SQL Server e banco de dados do SQL Azure. DMA recomenda melhorias de desempenho e confiabilidade para seu ambiente de destino e permite que você mova seu esquema, dados e objetos dependentes do servidor de origem para o servidor de destino.

> [!NOTE] 
> Para grandes (em termos de número e tamanho dos bancos de dados) migrações, é recomendável usar o [serviço de migração de banco de dados do Azure](https://docs.microsoft.com/azure/dms/dms-overview), que pode migrar bancos de dados em grande escala.
  
## <a name="capabilities"></a>Recursos

- Avalie as instâncias do SQL Server local migrando para bancos de dados do SQL Azure. O fluxo de trabalho de avaliação ajuda a detectar os seguintes problemas que podem afetar a migração de banco de dados do SQL Azure e fornece instruções detalhadas sobre como resolvê-los.

  - Problemas de bloqueio de migração: detecta os problemas de compatibilidade que migrar do bloco no SQL Server local bancos de dados s para bancos de dados do SQL Azure. DMA fornece recomendações para ajudá-lo a resolver esses problemas.

  - Suporte parcial ou recursos sem suporte: detecta parcialmente com suporte ou não há suporte para recursos que estão atualmente em uso na instância do SQL Server de origem. DMA fornece que um conjunto abrangente de recomendações, abordagens alternativas disponíveis no Azure e etapas atenuantes para que você pode incorporar em seus projetos de migração.

- Descubra os problemas que podem afetar uma atualização para um SQL Server local. Esses são descritas como problemas de compatibilidade e são organizados nas seguintes categorias:

  - Alterações mais recentes
  - Alterações de comportamento
  - Recursos preteridos

- Descubra novos recursos na plataforma do SQL Server de destino que pode se beneficiar do banco de dados após uma atualização. Esses são descritas como recomendações do recurso e são organizados nas seguintes categorias:

  - Desempenho
  - Segurança
  - Armazenamento

- Migre uma instância do SQL Server local para uma instância do SQL Server moderna, hospedada no local ou em uma máquina virtual do Azure (VM) que é acessível a partir de sua rede local. A VM do Azure podem ser acessada usando VPN ou outras tecnologias. O fluxo de trabalho de migração ajuda a migrar os seguintes componentes:

  - Esquema de bancos de dados
  - Dados e usuários
  - Funções de servidor
  - Logons do SQL Server e do Windows

- Após a migração bem-sucedida, aplicativos podem se conectar a bancos de dados do servidor SQL de destino diretamente.

## <a name="supported-source-and-target-versions"></a>Versões com suporte de origem e destino

DMA substitui todas as versões anteriores do Supervisor de atualização do SQL Server e deve ser usado para atualizações para a maioria das versões do SQL Server. Execute as versões com suporte de origem e destino.

**Fontes**
- SQL Server 2005
- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012 
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 no Windows

**Destinos**
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 no Windows e Linux
- Banco de dados SQL do Azure

> [!NOTE] 
> DMA atualmente não dá suporte gerenciado instância do banco de dados do SQL Azure como um destino.

## <a name="installation"></a>Instalação

Para instalar o DMA, baixe a versão mais recente da ferramenta do [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53595)e, em seguida, execute o **DataMigrationAssistant.msi** arquivo.

## <a name="see-also"></a>Confira também

[Avaliar sua migração do SQL Server](../dma/dma-assesssqlonprem.md)

[Assistente de migração de dados: Definições de configuração](../dma/dma-configurationsettings.md)

[Migrar local SQL Server usando o Assistente de migração de dados](../dma/dma-migrateonpremsql.md)

[Assistente de migração de dados: Práticas recomendadas](../dma/dma-bestpractices.md)



