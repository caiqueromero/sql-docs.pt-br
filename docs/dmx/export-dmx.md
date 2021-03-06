---
title: EXPORTAÇÃO (DMX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- EXPORT
dev_langs:
- DMX
helpviewer_keywords:
- exporting mining models
- exporting mining structures
- mining structures [DMX], exporting
- EXPORT statement
ms.assetid: 97617071-e560-4080-81af-a80276fc0823
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 2d3aa62213e15dbc7ca826a55e8b901fc5b9d038
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="export-dmx"></a>EXPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Extrai um modelo de mineração ou objeto de estrutura de mineração do servidor para um arquivo .abf (Analysis Services Backup).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Argumentos  
 *Tipo de objeto*  
 Opcional o tipo de objeto a ser exportado (modelo de mineração ou estrutura de mineração).  
  
 *Nome do objeto*  
 Opcional. Nome do objeto a ser exportado.  
  
 *filename*  
 Nome e local do arquivo a ser exportado como cadeia de caracteres.  
  
## <a name="remarks"></a>Remarks  
 Se a instrução especificar um modelo de mineração, o arquivo resultante também conterá uma estrutura de mineração associada. Se a declaração especifica **com dependências**, todos os objetos necessários para processar o objeto (por exemplo, a fonte de dados e a exibição da fonte de dados) são incluídos no arquivo. abf.  
  
 Você deve ser um banco de dados ou administrador do servidor para exportar ou importar objetos de um [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] banco de dados.  
  
## <a name="export-mining-structure-example"></a>Exemplo de estrutura de mineração de exportação  
 O exemplo a seguir exporta as estruturas de mineração Targeted Mailing e Forecasting, e o modelo de mineração Association para um local de arquivo específico. Como o modelo Association integra a estrutura de mineração de Market Basket, o exemplo exporta igualmente a estrutura Market Basket. Outros modelos de mineração que existam como parte da estrutura de mineração cesta não será exportado, porque o modelo de associação foi exportado usando **modelo de MINERAÇÃO**, não **estrutura de MINERAÇÃO**.  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Exemplo de modelo de mineração de exportação  
 O exemplo a seguir exporta o modelo de mineração de Associação para um local de arquivo especificado. Como a instrução especifica **com dependências**, a fonte de dados e objetos de exibição de fonte de dados também estão incluídos no arquivo. abf.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>Consulte também  
 [Extensões de mineração de dados &#40;DMX&#41; instruções de definição de dados](../dmx/dmx-statements-data-definition.md)   
 [Extensões de mineração de dados &#40;DMX&#41; instruções de manipulação de dados](../dmx/dmx-statements-data-manipulation.md)   
 [Extensões de mineração de dados & #40; DMX & #41; Referência de instrução](../dmx/data-mining-extensions-dmx-statements.md)   
 [IMPORTAÇÃO &AMP;#40;DMX&AMP;#41;](../dmx/import-dmx.md)   
 [Exportar e importar objetos de mineração de dados](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
