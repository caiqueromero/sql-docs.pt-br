---
title: Iniciar valores do gráfico de pizza na parte superior da pizza (Construtor de Relatórios e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e2f3e37e01aa49e3c868696011cf446cb13665f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>Iniciar valores do gráfico de pizza na parte superior da pizza (Construtor de Relatórios e SSRS)
Em gráficos de pizza de relatórios paginados do [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , o primeiro valor do conjunto de dados inicia a 90 graus da parte superior da pizza por padrão. 

![report-builder-pie-chart-start-at-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*Os valores do gráfico começam em 90 graus.*

Em vez disso, pode ser útil deixar o primeiro valor iniciar na parte superior. 

![report-builder-pie-chart-start-at-top](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*Gráficos de pizza começam na parte superior do gráfico.*
  
## <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>Para iniciar o gráfico de pizza na parte superior da pizza  
  
1.  Clique na própria pizza.  
  
2.  Se o painel **Propriedades** não for aberto, na guia **Exibição** , clique em **Propriedades**.  
  
3.  No painel **Propriedades** , sob **Atributos Personalizados**, altere **PieStartAngle** de **0** para **270**.  
  
4.  Clique em **Executar** para visualizar o relatório.  
  
 O primeiro valor agora inicia na parte superior do gráfico de pizza.  
  
## <a name="see-also"></a>Consulte Também  
 [Formatando um gráfico &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Gráficos de pizza &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  
