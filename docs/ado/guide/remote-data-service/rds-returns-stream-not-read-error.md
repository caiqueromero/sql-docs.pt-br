---
title: "RDS retornará &quot;fluxo não leitura&quot; erro | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b5c0cbc0d8c83a2d36fc931616046b0261938a0a
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS retornará &quot;fluxo não leitura&quot; erro
"A objeto de fluxo não foi possível ler porque ele está vazio ou a posição atual está no final do fluxo. Para fluxos de não vazio, defina a posição atual com a propriedade de posição. Para determinar se um fluxo está vazio, verifique a propriedade de tamanho."  
  
 Se você vir essa mensagem de erro, você pode ter tentado usar uma consulta parametrizada de hierárquica via http. RDS não permite que você usar hierarquias com parâmetros remotas.  
  
> [!IMPORTANT]
>  Começando com o Windows 8 e Windows Server 2012, os componentes de servidor RDS não estão mais incluídos no sistema operacional Windows (veja o Windows 8 e [manual de compatibilidade do Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obter mais detalhes). Componentes de cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Aplicativos que usam o RDS devem migrar para [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos básicos do RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


