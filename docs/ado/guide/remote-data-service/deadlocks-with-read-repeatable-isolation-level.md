---
title: Deadlocks com o nível de isolamento Repeatable leitura | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks in RDS [ADO]
- read repeatable in RDS [ADO]
ms.assetid: 29f3683f-12f3-4304-8a54-fe133c25a423
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6fc1621022758189925587e32059a3e26a1de4a4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>Deadlocks com o nível de isolamento Repeatable de leitura
Se um objeto de negócios personalizada usa um nível de isolamento de leitura repetida para acessar um SQL Server e o objeto comercial é chamado simultaneamente por dois clientes que enviam uma consulta e atualização na mesma transação, um deadlock é possível. Serviço de dados remoto foi projetado para permitir que um dos processos de tempo limite para liberar o bloqueio, mas a atualização falhará para esse cliente.  
  
 Use o [serviço de Cursor](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) **tempo limite do comando** propriedade dinâmica para modificar o comprimento do tempo limite.  
  
> [!IMPORTANT]
>  Começando com o Windows 8 e Windows Server 2012, os componentes de servidor RDS não estão mais incluídos no sistema operacional Windows (veja o Windows 8 e [manual de compatibilidade do Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obter mais detalhes). Componentes de cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Aplicativos que usam o RDS devem migrar para [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos básicos do RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



