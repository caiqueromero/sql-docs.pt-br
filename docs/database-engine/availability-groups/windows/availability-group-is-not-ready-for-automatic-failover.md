---
title: O grupo de disponibilidade não está pronto para o failover automático | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c99a7d813b190823c28b50daa4b50f1d6b2c6b1
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34771322"
---
# <a name="availability-group-is-not-ready-for-automatic-failover"></a>O grupo de disponibilidade não está pronto para o failover automático
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Introdução  
  
|||  
|-|-|  
|**Nome da Política**|Prontidão para Failover Automático do Grupo de Disponibilidade|  
|**Problema**|O grupo de disponibilidade não está pronto para o failover automático.|  
|**Categoria**|**Crítico**|  
|**Faceta**|grupo de disponibilidade|  
  
## <a name="description"></a>Descrição  
 Esta política verifica se o grupo de disponibilidade tem ao menos uma réplica secundária pronta para failover. A política estará em estado não íntegro e um alerta será emitido quando o modo de failover da réplica primária for automático, mas nenhuma das réplicas secundárias do grupo de disponibilidade está pronta para failover.  
  
 A política estará em estado íntegro quando pelo menos uma réplica secundária estiver pronta para failover automático.  
  
> [!NOTE]  
>  Para esta versão do [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], as informações sobre as possíveis causas e soluções estão localizadas em [O grupo de disponibilidade não está pronto para failover automático](http://go.microsoft.com/fwlink/p/?LinkId=220851) no Wiki do TechNet.  
  
## <a name="possible-causes"></a>Causas possíveis  
 O grupo de disponibilidade não está pronto para o failover automático. A réplica primária está configurada para failover automático; porém, a réplica secundária não está pronta para failover automático. A réplica secundária que está configurada para failover automático pode estar indisponível ou seu estado de sincronização de dados não é atualmente SYNCHRONIZED.  
  
## <a name="possible-solutions"></a>Soluções possíveis  
 Estas são as possíveis soluções para este problema:  
  
-   Verifique se pelo menos uma réplica secundária está configurada como failover automático. Se não houver uma réplica secundária configurada como failover automático, atualize a configuração de uma réplica secundária para ser o destino de failover automático com confirmação síncrona.  
  
-   Use a política para verificar se os dados estão em estado de sincronização e se o destino de failover automático é SYNCHRONIZED, e depois resolva o problema na réplica de disponibilidade.  
  
## <a name="see-also"></a>Consulte Também  
 [Visão geral dos grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usar o Painel AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
