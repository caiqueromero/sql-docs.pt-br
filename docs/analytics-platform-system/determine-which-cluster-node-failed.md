---
title: Determinar o nó de cluster com falha - Analytics Platform System | Microsoft Docs
description: Este artigo descreve como determinar o nome do nó Analytics Platform System (APS) que apresentou falha após um failover de cluster ocorreu e um alerta de failover de cluster foi ativado. Como parte de um cluster de failover de solução de problemas, você deve determinar o nome do nó com falha antes de entrar em contato com a Microsoft para ajudar a resolver o problema.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 031c8033e91d7a7f74ca8c4409bc02296a22ebcf
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="determine-which-cluster-node-failed-for-analytics-platform-system"></a>Determinar qual cluster do nó falhou para Analytics Platform System
Este tópico descreve como determinar o nome do nó Analytics Platform System (APS) que apresentou falha após um failover de cluster ocorreu e um alerta de failover de cluster foi ativado. Como parte de um cluster de failover de solução de problemas, você deve determinar o nome do nó com falha antes de entrar em contato com a Microsoft para ajudar a resolver o problema.  
  
## <a name="Background"></a>Plano de fundo  
Para alta disponibilidade no SQL Server PDW, o nó de controle e os nós de computação são configurados como ativos ou passivos componentes de clusters de failover do Windows. Quando um servidor ativo não responder a solicitações de sistema críticos, o servidor passivo failover e executa as funções de servidor que falhou.  
  
Após um failover de cluster, quando o SQL Server PDW relata status de nó, o servidor passivo tem uma falha sobre status. No entanto, não é óbvio qual servidor ou nó falha, especialmente se o servidor que não ainda estiver online. Para solucionar a falha do cluster, você deve determinar o nome do nó que falhou.  
  
## <a name="AdminConsoleSolution"></a>Solução do Console de administração  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>Para localizar o nome do nó com falha  
  
1.  Abra o Console do administrador. Para obter mais informações sobre o Console de administração, consulte [monitorar o dispositivo usando o Console de administração &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). Após o failover, o evento de failover está incluído no número de alertas sobre o **integridade** página. Há um **integridade** página para a região PDW, região HDI e para a região de malha do dispositivo. Cada página de integridade tem um **alertas** guia. Para saber mais sobre um alerta, clique na página de integridade, a guia alertas e, em seguida, clique em um alerta.  
  
## <a name="SystemView"></a>Solução de modo de exibição do sistema  
A instrução SQL a seguir mostra como usar o [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md) exibição do sistema para localizar o nome do servidor que falhou.  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
