---
title: Web part do Visualizador de Relatórios em um site do SharePoint – SSRS | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server-sharepoint
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c29118ab8807d8bd0d51ee593488c66c89bf2942
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="report-viewer-web-part-on-a-sharepoint-site---reporting-services"></a>Web part do Visualizador de Relatórios em um site do SharePoint – Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

A web part do Visualizador de Relatórios é uma web part personalizada. Use a web part para exibir, navegar, imprimir e exportar relatórios de um servidor de relatório em um site do SharePoint. A web part do Visualizador de Relatórios está associada a arquivos de definição de relatório (.rdl) processados por um servidor de relatório do Microsoft SQL Server Reporting Services. 

A última web part do Visualizador de relatórios também pode entregar relatórios paginados implantados em um Servidor de Relatórios do Power BI. A web part não funciona com relatórios do Power BI.

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>Por que a web part do Visualizador de Relatórios foi lançada novamente

A web part do Visualizador de Relatórios estava disponível como parte do Suplemento Reporting Services para produtos do SharePoint. A web part era específica a servidores de relatório no modo integrado do SharePoint. O modo integrado do SharePoint foi preterido após o SQL Server 2016.

A partir do SQL Server 2017, há apenas um modo de instalação do Reporting Services: **modo Nativo**. Você pode inserir todos os tipos de relatórios usando uma web part do Visualizador de Páginas usando o parâmetro de URL *rs:Embed=true*. A inserção de relatórios em páginas do SharePoint é uma história de integração solicitada por clientes e a web part do Visualizador de Relatórios atualizada possibilita esse cenário para relatórios paginados.

Embora a web part do Visualizador de Páginas seja suficiente para inserir um relatório paginado em uma página do SharePoint, a web part do Visualizador de Relatórios atualizada oferece recursos adicionais.

* Mostrar/ocultar botões específicos da barra de ferramentas
* Substituir valores de parâmetro de relatório
* Conectar web parts de Filtro a parâmetros de relatório

## <a name="download-the-report-viewer-web-part-solution-package"></a>Baixar o pacote de solução da web part do Visualizador de Relatórios

A web part do Visualizador de Relatórios está disponível no Centro de Download da Microsoft.

[Baixar o pacote de solução da web part do Visualizador de Relatórios](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>Considerações e limitações

Os itens listados são específicos à web part do Visualizador de Relatórios atualizada.

* A web part só pode ser usada em páginas *clássicas* do SharePoint.
* Há suporte apenas para relatórios paginados (RDL) na inserção na web part do Visualizador de Relatórios. Se desejar inserir relatórios ou relatórios móveis do Power BI, use o parâmetro de URL *rs:Embed=true*.

## <a name="next-steps"></a>Próximas etapas

Para começar a usar a web part do Visualizador de Relatórios atualizada, consulte [Implantar a web part do Visualizador de Relatórios em um site do SharePoint](deploy-report-viewer-web-part.md).
