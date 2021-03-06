---
title: Conformidade XML for Analysis (XMLA) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b618fdd8cca3faed72afb0276f18cd928a3f31f7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576878"
---
# <a name="xml-for-analysis-xmla-compliance"></a>Conformidade XML for Analysis (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]  

  A especificação XML for Analysis 1.1 descreve um padrão aberto que aceita acesso a fontes de dados que residem na World Wide Web. Este tópico fornece detalhes sobre o nível de conformidade com a especificação XML for Analysis 1.1 que é suportada pelo Azure Analysis Services e SQL Server Analysis Services.  
  
## <a name="compliant-items"></a>Itens de conformidade  
Analysis Services está em conformidade com todos os itens obrigatórios listados na especificação XML for Analysis 1.1. Além disso, o Analysis Services implementa o item opcional a seguir descrito na especificação XML for Analysis 1.1.  
  
|Item|Especificação|Implementação|  
|----------|-------------------|--------------------|  
|Suporte de sessão|Os elementos de cabeçalho SOAP estão listados na seção "Suporte para a capacidade de manutenção de status do processo em XML for Analysis" da especificação XML for Analysis 1.1.|Todos os elementos de cabeçalho SOAP listados têm suporte pelo Analysis Services, conforme descrito na especificação.|  
  
## <a name="extensions"></a>Extensões  
 Analysis Services também estende a especificação XML for Analysis 1.1 para oferece suporte aos seguintes recursos adicionais e recursos.  
  
|Item|Especificação|Implementação|  
|----------|-------------------|--------------------|  
|Negociação de protocolo|Nenhuma informações contida na especificação XML for Analysis 1.1 |Elemento de cabeçalho ProtocolCapabilities adicionado pelo Analysis Services para dar suporte a negociação de recursos de protocolo.|  
|Comandos do XMLA (XML for Analysis) aceitos pelo método Discover|Os comandos a seguir têm suporte na especificação XML for Analysis 1.1:<br /><br /> [Elemento de instrução &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Os comandos a seguir são suportados pelo Analysis Services:<br /><br /> [Elemento ALTER &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Elemento de backup &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [Elemento de lote &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [Elemento BeginTransaction &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Elemento Cancel &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [Elemento ClearCache &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [Elemento CommitTransaction &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [Criar elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Elemento Delete &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [Elemento DesignAggregations &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Elemento drop &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [Elemento Insert &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Bloquear elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [Elemento MergePartitions &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [Elemento NotifyTableChange &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Processar o elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Elemento Restore &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [Elemento RollbackTransaction &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Elemento de instrução &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [Elemento Subscribe &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Elemento Synchronize &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [Elemento Unlock &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Elemento Update &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [Elemento UpdateCells &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Erros de coluna em conjuntos de linhas tabulares|Não listado na especificação XML for Analysis 1.1.|O [erro](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) elemento é usado pelo Analysis Services para relatar erros para elementos de coluna contidos em um [linha](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) elemento.|  
  
## <a name="see-also"></a>Confira também
 [Referência de XML for Analysis &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
