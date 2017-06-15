---
title: O que &#39; s novo no Reporting Services (SSRS) | Microsoft Docs
ms.date: 05/30/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- what's new [Reporting Services]
- Reporting Services, what's new
- SQL Server Reporting Services, what's new
- SSRS, what's new
ms.assetid: bc909063-6b84-4b3a-80d2-e93fc04b4b9d
caps.latest.revision: 206
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 7428fd46c73c7e32814928ae95085a704167544d
ms.contentlocale: pt-br
ms.lasthandoff: 06/13/2017

---
# <a name="what39s-new-in-sql-server-reporting-services-ssrs"></a>O que &#39; s novos no SQL Server Reporting Services (SSRS)
Saiba mais sobre o que há de novo no SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Isso aborda as principais áreas de recurso e é atualizado à medida que novos itens são lançados.
  
  Para obter informações sobre o que há de novo em outras áreas do SQL Server, consulte [Novidades no SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md) ou [o que há de novo no SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).
  
 **Download** ![download](../analysis-services/media/download.png "download")
 
- Para fazer o download da Visualização Técnica de janeiro de 2017 dos relatórios do Power BI no SQL Server Reporting Services, junto com a versão de área de trabalho do Power BI (SQL Server Reporting Services), vá para o **[Centro de downloads da Microsoft](https://go.microsoft.com/fwlink/?linkid=839351)**.
  
-   Para baixar o [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], acesse o  **[Centro de Avaliação](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
  
-   Tem uma conta do Azure?  Em seguida, acesse  **[aqui](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016sp1enterprisewindowsserver2016/)**  para criar uma máquina Virtual com o SQL Server já instalado.  

 ![Observação](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "Observação") para obter as notas de versão atual, consulte [notas de versão do SQL Server 2016](../sql-server/sql-server-2016-release-notes.md) ou [notas de versão do servidor de relatório do Power BI](https://powerbi.microsoft.com/documentation/reportserver-release-notes/).

Para obter informações sobre o servidor de relatório do Power BI, consulte [Introdução ao servidor de relatório do Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

## <a name="query-designer-support-for-dax-now-in-report-builder-and-sql-server-data-tools"></a>Consultar o suporte do designer de DAX agora no construtor de relatórios e o SQL Server Data Tools

Nas versões mais recentes do construtor de relatórios e o SQL Server Data Tools – versão Release Candidate, agora você pode criar consultas DAX nativo em modelos de dados de tabela do SQL Server Analysis Services com suporte. Você pode usar o designer de consulta em ambas as ferramentas para arrastar e soltar os campos que você deseja e fazer a consulta DAX gerada para você, em vez de gravá-la.  
 
Leia mais sobre o [blog do Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/).

* Baixar [construtor de relatórios do SQL Server 2016](https://go.microsoft.com/fwlink/?LinkId=734968).
* Baixar [SQL Server Data Tools – versão Release Candidate](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools-ssdt-release-candidate).

> **Observação**: você só pode usar o designer de consulta para DAX com fontes de dados de tabela do SSAS criadas no SQL Server 2016 +.
 
## <a name="whats-new-in-sql-server-2016"></a>Novidades no SQL Server 2016
  
### <a name="reporting-services-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>Reporting Services [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]  
 Um novo [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] está disponível. Esse é um portal atualizado e moderno, que incorpora KPIs, Relatórios Móveis, Relatórios Paginados e arquivos do Excel e Power BI Desktop. O [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] substitui o Gerenciador de Relatórios de versões anteriores. Você também pode baixar o Publicador de Relatórios Móveis e o Construtor de Relatórios do [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] sem precisar da tecnologia ClickOnce.
 
 Para criar Relatórios Móveis, você precisará do [!INCLUDE[SS_MobileReptPub_Short](../includes/ss-mobilereptpub-short-md.md)].  
  
 Para saber mais sobre o [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)], veja o [Portal da Web SSRS Modo Nativo](../reporting-services/web-portal-ssrs-native-mode.md).  
  
 ![ssRSPortal](../reporting-services/media/ssrsportal.png "ssRSPortal")  
 
 #### <a name="custom-branding-for-the-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>Identidade visual personalizada para o [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 
  Você pode personalizar o [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] com o logotipo e cores da sua organização usando um pacote de identidade visual.  
  
  Para obter mais informações sobre identidade visual personalizada, consulte [Identidade visual do portal da Web](http://msdn.microsoft.com/en-us/6dac97f7-02a6-4711-81a3-e850a6b40bf1)
 
 #### <a name="key-performance-indicators-kpi-in-the-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>KPI (indicadores chave de desempenho) [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 

Você pode criar KPIs contextuais para a pasta em que você está diretamente no [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] . Ao criar KPIs, você pode escolher campos de conjunto de dados e resumir esses valores. Você também pode selecionar o conteúdo relacionado a drill-through para obter mais detalhes.
  
 ![ssrs-webportal-kpi](../reporting-services/media/ssrs-webportal-kpi.png)
 
 Para obter mais informações, consulte [Trabalhando com KPIs no portal da Web](http://msdn.microsoft.com/en-us/a28cf500-6d47-4268-a248-04837e7a09eb)
  
 
 ### <a name="mobile-reports"></a>Relatórios móveis
 
Os relatórios móveis do Reporting Services são relatórios dedicados e otimizado para uma ampla variedade de fatores forma que proporcionam uma melhor experiência para usuários que acessam relatórios em dispositivos móveis. Relatórios móveis apresentam uma variedade de visualizações, desde gráficos de tempo, de categoria e de comparação, mapas de árvores e personalizados. Conecte seus relatórios móveis a uma variedade de fontes de dados, incluindo dados multidimensionais e tabulares do SQL Server Analysis Services local. Disponha seus relatórios móveis em uma superfície de design com colunas e linhas de grade ajustáveis e elementos de relatório móvel flexíveis que se adaptam bem a qualquer tamanho de tela. Salve esses relatórios móveis em um servidor do Reporting Service para exibir e interagir com eles em um navegador ou no aplicativo móvel do Power BI em iPads, iPhones, smartphones Android e dispositivos Windows 10.
  
#### <a name="mobile-report-publisher"></a>Publicador de Relatórios Móveis  
 O [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)]permite a você criar e publicar relatórios móveis do SQL Server para seu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)].  
  
 ![SS_MRP_LayoutTabSmall](../reporting-services/media/ss-mrp-layouttabsm.png "SS_MRP_LayoutTabSmall")  
  
 Para obter mais informações, consulte [Criar relatórios móveis com o Publicador de Relatórios Móveis do SQL Server](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md).  
  
#### <a name="sql-server-mobile-reports-hosted-in-reporting-services-available-in-power-bi-mobile-app"></a>Relatórios móveis do SQL Server hospedados no Reporting Services disponíveis no aplicativo móvel do Power BI  
 O aplicativo móvel do Power BI para iOS no iPad e iPhone agora pode exibir relatórios móveis do SQL Server hospedados no seu servidor de relatório local.  
  
 ![SS_MRP_iPad_HomeSm](../reporting-services/media/ss-mrp-ipad-homesm.png "SS_MRP_iPad_HomeSm")  
  
 Você não pode se conectar, por padrão, sem algumas alterações de configuração. Para saber mais sobre como permitir que o aplicativo móvel do Power BI se conecte ao seu servidor de relatório, veja [Enable a report server for Power BI Mobile access](../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md).
  
### <a name="support-of-sharepoint-mode-and-sharepoint-2016"></a>Modo de suporte ao SharePoint e SharePoint 2016.  
 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supports integration with SharePoint 2013 and SharePoint 2016.
 
Para obter mais informações, consulte:  
  
-   [Combinações do SharePoint e do servidor e suplemento Reporting Services com suporte &#40;SQL Server 2016&#41;](../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
-   [Onde encontrar o suplemento Reporting Services para produtos do SharePoint](../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Instalar o Reporting Services no modo do SharePoint](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  

### <a name="microsoft-net-framework-4-support"></a>Suporte ao Microsoft .NET Framework 4  
 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] dá suporte à versão atual do Microsoft .NET Framework 4. Isso inclui a versão 4.0 e 4.5.1. Se nenhuma versão do .Net Framework 4.x estiver instalada, a configuração do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instalará o .NET 4.0 durante a etapa de instalação do recurso.  

### <a name="report-improvements"></a>Aprimoramentos de relatórios

**Mecanismo de Renderização HTML 5:** Um novo mecanismo de renderização HTML5 que se destina ao modo de padrões "completo" da Web moderna e navegadores modernos.  O novo mecanismo de renderização não depende do modo quirks usado por alguns navegadores mais antigos.
  
 Para obter mais informações sobre o suporte ao navegador, veja [Suporte ao navegador para Reporting Services e Power View](../reporting-services/browser-support-for-reporting-services-and-power-view.md).  

**Relatórios paginados modernos:** desenvolva relatórios paginados modernos perfeitos com estilos novos e modernos para gráficos, medidores, mapas e outras visualizações de dados.
  
**Gráficos explosão solar e mapa de árvore:** Aprimore seus relatórios com mapa de árvore ![ssrs_treemap_icon](../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon") e explosão solar ![ssrs_sunburst_icon](../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon") gráficos, excelentes maneiras de exibir dados hierárquicos. Para saber mais, confira [Tree Map and Sunburst Charts in Reporting Services](../reporting-services/report-design/tree-map-and-sunburst-charts-in-reporting-services.md).  

**Inserção de relatório:** agora você pode incorporar relatórios móveis e paginados a outras páginas da Web e aplicativos usando um iframe juntamente com os parâmetros da URL.  

**Fixar itens de relatórios a um Painel do Power BI:** Ao exibir um relatório no [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], você pode selecionar itens de relatório e fixá-los a um painel do [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .   Os itens que você pode fixar são gráficos, painéis de medidores, mapas e imagens. Você pode selecionar **(1)** o grupo que contém o painel que você quer fixar, **(2)** selecionar o painel no qual você quer fixar o item e **(3)** selecionar a frequência com que você quer que o bloco seja atualizado no painel.   ![Observação](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "Observação") a atualização é gerenciada pelo [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] assinaturas e depois que o item é fixado, você pode editar a assinatura e configurar uma agenda de atualização diferentes.  
  
 ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png) 
  
 Para obter mais informações, consulte [Integração do Servidor de Relatório do Power BI &#40;Configuration Manager&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md) e [Fixar itens do Reporting Services nos painéis do Power BI](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md).  
 
 **Renderização e exportação do PowerPoint:** o formato Microsoft PowerPoint (PPTX) é uma nova extensão de renderização do [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]. Você pode exportar relatórios no formato PPTX de aplicativos comuns; Construtor de Relatórios, Designer de Relatórios (no SSDT) e o [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Por exemplo, a imagem a seguir mostra o menu de exportação do [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. 
  
 ![ssrs-export-powerpoint](../reporting-services/media/ssrs-export-powerpoint.png) 
  
 Você também pode selecionar o formato PPTX para saída de assinatura e usar o acesso à URL do Servidor de Relatório para renderizar e exportar um relatório. Por exemplo, o seguinte comando de URL no seu navegador exporta um relatório de uma instância nomeada do servidor de relatório.  
  
```  
http://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 Para saber mais, confira [Export a Report Using URL Access](../reporting-services/export-a-report-using-url-access.md).  
 
 **PDF substitui o ActiveX para Impressão Remota:** A experiência de impressão do ActiveX da barra de ferramentas do visualizador de relatórios foi substituída por uma experiência moderna baseada em PDF que funciona na matriz dos navegadores com suporte, incluindo o Microsoft Edge. Não é mais necessário baixar os controles do ActiveX! Dependendo do navegador que você usa e dos aplicativos e serviços de visualização de PDF que você tenha instalados, o [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] abrirá um diálogo de impressão para imprimir o seu relatório ou solicitará que você baixe um arquivo .PDF do seu relatório.  Como administrador, você ainda pode desabilitar impressão do lado do cliente do [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Para obter mais informações, consulte [Habilitar e desabilitar a impressão do lado do cliente para Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).

![ssrs-pdf-printing](../reporting-services/media/ssrs-pdf-printing.png)

### <a name="subscription-improvements"></a>Aprimoramentos de Assinatura  
 
|Recurso|Modo de servidor com suporte|  
|-------------|---------------------------|  
|**Habilitar e desabilitar assinaturas**. Novas opções de interface de usuário para desabilitar e habilitar rapidamente as assinaturas. As assinaturas desabilitadas mantêm suas outras propriedades de configuração, como o cronograma, e podem ser facilmente habilitadas.<br /><br /> ![ssrs-enable-disable-subscriptions](../reporting-services/media/ssrs-enable-disable-subscriptions.png)<br /><br /> Para saber mais, confira [Disable or Pause Report and Subscription Processing](../reporting-services/subscriptions/disable-or-pause-report-and-subscription-processing.md).|Modo nativo|  
|**Descrição da assinatura**. Quando você cria uma nova assinatura, você pode incluir uma descrição do relatório como parte das propriedades de assinatura. A descrição será incluída na página de resumo da assinatura.|Modo do SharePoint e Nativo|  
|**Alterar o proprietário da assinatura**. Interface de usuário aprimorada para alterar rapidamente o proprietário de uma assinatura. As versões anteriores do [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] permitem que os administradores alterem os proprietários de assinatura usando o script. A partir da versão [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] , você pode alterar os proprietários da assinatura usando a interface do usuário ou o script. Alterar o proprietário da assinatura é uma tarefa administrativa comum quando os usuários deixam ou alteraram funções em sua organização.|Modo do SharePoint e Nativo|  
|**Credenciais compartilhadas para assinaturas de compartilhamento de arquivos**. Agora existem dois fluxos de trabalho com as assinaturas de compartimento de arquivos do [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] :<br /><br /> Novidades desta versão, o administrador do [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pode configurar uma conta única de compartilhamento de arquivo, que é usada para várias assinaturas. A conta de compartilhamento de arquivo é configurada no gerenciador de configuração do modo nativo do [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] **Especificar uma conta de compartilhamento de arquivo**e, em seguida, na página de configuração da assinatura, os usuários selecionam **Usar uma conta de compartilhamento de arquivo**.<br /><br /> Configure assinaturas individuais com credenciais específicas para o compartilhamento de arquivos de destino.<br /><br /> Você também pode combinar as duas abordagens e fazer com que algumas assinaturas de compartilhamento de arquivos usem a conta de compartilhamento de arquivos central, enquanto outras assinaturas usam credenciais específicas.|Modo nativo|  

### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
 A nova versão do SSDT inclui os modelos de projeto para o [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]: Assistente de Projeto do Servidor de Relatório e Projeto do Servidor de Relatório. Para saber mais sobre como baixar o SSDT, veja [Ferramentas de Dados do SQL Server para Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkId=827542).  

### <a name="report-builder-improvements"></a>Aprimoramentos do Construtor de Relatórios

**Nova interface de usuário do Construtor de Relatórios:** a principal interface de usuário do [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] agora tem uma aparência moderna com elementos de interface do usuário simplificados.  
  
|||  
|-|-|  
|Nova|Previous|  
|![ssrs_rbfacelift_new](../reporting-services/media/ssrs-rbfacelift-new.png "ssrs_rbfacelift_new")|![ssrs_rbfacelift_old](../reporting-services/media/ssrs-rbfacelift-old.png "ssrs_rbfacelift_old")|  

**Painel de parâmetros personalizado:** agora você pode personalizar o painel de parâmetros. Usando a superfície de design no Construtor de Relatórios, você pode arrastar um parâmetro para uma coluna e linha específica no painel de parâmetros. Você pode adicionar e remover colunas para alterar o layout do painel.   Para obter mais informações, consulte [Personalizar o painel de parâmetros em um relatório &#40;Construtor de Relatórios&#41;](../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
 ![Lista de parâmetros no painel de dados de relatório e, no painel de parâmetros](../reporting-services/media/ssrs-customizeparameter-parameterlist-reportdatapane.png "lista de parâmetros no painel de dados de relatório e, no painel de parâmetros")  

  
**Suporte a alto DPI:** [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] oferece suporte a dispositivos e dimensionamento de alto DPI (pontos por polegada).  Para saber mais sobre Alto DPI, veja o seguinte:  
  
-   [Aprimoramentos de dimensionamento de DPI do Windows 8.1](https://blogs.windows.com/windowsexperience/2013/07/15/windows-8-1-dpi-scaling-enhancements/)  
  
-   [Alto DPI e Windows 8.1](http://technet.microsoft.com/library/dn528848.aspx)  

## <a name="next-steps"></a>Próximas etapas

[Novidades do Analysis Services](http://msdn.microsoft.com/en-us/aa69c299-b8f4-4969-86d8-b3292fe13f08)  
[Visualização Técnica dos relatórios do Power BI no SSRS - Notas de versão](../reporting-services/reporting-services-release-notes.md)  
[Notas de Versão do SQL Server 2016.](../sql-server/sql-server-2016-release-notes.md)   
[Compatibilidade com versões anteriores](http://msdn.microsoft.com/en-us/675b0e0e-cfee-4790-9675-80fc3ea6d30f)   
[Recursos do Reporting Services com suporte nas edições do SQL Server 2016](http://msdn.microsoft.com/en-us/39f03d2d-6e48-4b34-a9d3-07f86313b937)   
[Atualizar e migrar o Reporting Services](../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
[Servidor de relatórios de BI de energia](https://powerbi.microsoft.com/documentation/reportserver-get-started/)  

Mais perguntas? [Tente fazer o fórum do Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)