---
title: Propriedade PropertyType (classe ClientNetworkProtocolProperty) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PropertyType Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyType property
ms.assetid: fc0e4725-979f-4517-a8f5-25436b87f5c2
caps.latest.revision: 30
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: db54a9d67461540f3e87f14fef5c9df19e24ce57
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="propertytype-property-clientnetworkprotocolproperty-class"></a>Propriedade PropertyType (classe ClientNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtém o tipo da propriedade atual referenciado pelo valor [PropertyIdx Property (classe ClientNetworkProtocolProperty) (classe ClientNetworkProtocolProperty)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.PropertyType [= value]  
```  
  
## <a name="parts"></a>Partes  
 *objeto*  
 A [classe ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) que representa um atributo do protocolo de rede usado pelo cliente do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/Valor do retorno  
 Um valor **uint32** que especifica o tipo de dado da propriedade.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Consulte também  
 [Configurar protocolos de cliente](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
