---
title: Propriedades personalizadas da origem XML | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e5e85d8fa58235f3fb13c0cc3fbc237f6f104a8b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="xml-source-custom-properties"></a>Propriedades personalizadas da origem XML
  A origem XML contém propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da origem XML. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de Dados|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|O modo usado para acessar os dados XML.|  
|UseInlineSchema|Booliano|Um valor que indica se deve ser usada uma definição de esquema embutido dentro da origem XML. O valor padrão dessa propriedade é **False**.|  
|XMLData|Cadeia de caracteres|O arquivo ou variáveis dos quais é possível recuperar os dados XML.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
|XMLSchemaDefinition|Cadeia de caracteres|O caminho e nome de arquivo do arquivo de definição de esquema (.xsd).<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
  
 A tabela a seguir descreve as propriedades personalizadas da saída da origem XML. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de Dados|Description|  
|-------------------|---------------|-----------------|  
|RowsetID|Cadeia de caracteres|Um valor que identifica o conjunto de linhas associado à saída.|  
  
 As colunas de saída da origem XML não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [XML Source](../../integration-services/data-flow/xml-source.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Propriedades comuns](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
