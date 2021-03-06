---
title: Alterar o Tipo de Log de Transações de Entidade (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 75250b32-3384-43c2-9b5c-1607cc3aa7b3
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d981976b5a8e73ade7063c73eafb1d7a1b9dcd45
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="change-the-entity-transaction-log-type-master-data-services"></a>Alterar o Tipo de Log de Transações de Entidade (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Você pode alterar o tipo de log de transações de uma entidade para atributo, membro ou nenhum.  
  
|Tipo de Log de transações|Description|  
|--------------------------|-----------------|  
|attribute|Os logs de alteração de entidades são salvos no nível do atributo.<br /><br /> O log de transações é salvo, assim como para o [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].|  
|Membro|Os logs de alteração de entidades são salvos no nível de linha.<br /><br /> Qualquer alteração de atributo dispara uma nova revisão de linha.<br /><br /> Ao usar o tipo de log de transações de linha, a entidade será armazenada como uma dimensão de alteração lenta do Tipo 4. A exibição de assinatura do Tipo 2 e a exibição de assinatura (histórico) do Tipo 4 têm suporte. Para obter mais informações, consulte [Formatos de exibição de assinatura &#40;Master Data Services&#41;](../master-data-services/subscription-view-formats-master-data-services.md)<br /><br /> Oferece um melhor desempenho.|  
|Nenhum|Nenhum log de alteração é salvo.<br /><br /> Fornece o melhor desempenho.|  
  
## <a name="prerequisites"></a>Prerequisites  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional Administração do Sistema. Para obter mais informações, consulte [Permissões de área funcional &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   A entidade deve existir. Para obter mais informações, consulte [Criar uma entidade &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
 **Para alterar o tipo de log de transações**  
  
1.  No Master Data Manager, clique em **Administração do Sistema**.  
  
2.  Na página **Gerenciar Modelo** , selecione a linha do modelo da entidade que você deseja editar e clique em **Entidades**.  
  
3.  Na página **Gerenciar Entidade** , selecione a linha da entidade que deseja atualizar e clique em **Editar**.  
  
4.  Escolha o tipo de log de transações na lista suspensa.  
  
5.  Clique em **Salvar**.  
  
  
