---
title: Copiar e colar dados (SSAS Tabular) | Microsoft Docs
ms.custom: 
ms.date: 05/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.pastepreviewdb.f1
ms.assetid: 2f8d8b3d-810b-4c31-98f2-341015e13da8
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5bbc30ea67df15827da8b289fe1481beee0b6016
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="import-data---copy-and-paste-data"></a>Importar dados - copiar e colar dados
  É possível copiar dados de tabelas de aplicativos externos e colá-los em uma nova tabela ou uma existente no designer de modelo. Os dados colados da Área de Transferência devem estar em formato HTML, por exemplo, dados que são copiados de Excel ou Word. O designer de modelo detectará e aplicará automaticamente os tipos de dados aos dados colados. Você também pode modificar manualmente o tipo de dados ou a formatação de exibição de uma coluna.  
  
 Ao contrário de tabelas com uma conexão da fonte de dados, as tabelas coladas não têm uma propriedade Nome de Conexão ou Dados de Origem. Dados colados são persistidos no arquivo Model.bim. Quando o projeto ou o arquivo Model.bim for salvo, os dados colados também serão salvos.  
  
 Quando um modelo é implantado, os dados colados também serão implantados com ele, mesmo que o modelo não seja processado com a implantação.  
  
 Seções neste tópico:  
  
-   [Pré-requisitos](#bkmk_prerequisites)  
  
-   [Colar dados](#bkmk_paste_data)  
  
-   [Caixa de diálogo Colar Visualização](#bkmk_paste_preview)  
  
##  <a name="bkmk_prerequisites"></a> Pré-requisitos  
 Há algumas restrições para colar dados:  
  
-   As tabelas coladas não podem ter mais de 10.000 linhas.  
  
-   Não é possível particionar tabelas coladas.  
  
-   Tabelas coladas não têm suporte no modo DirectQuery.  
  
-   As opções **Colar Acréscimo** e **Colar Substituição** estão disponível somente para trabalhar com uma tabela que tenha sido inicialmente através da colagem de dados da Área de Transferência. Não é possível usar **Colar Acréscimo** ou **Colar Substituição** para adicionar dados em uma tabela de dados importados de outro tipo de fonte de dados.  
  
-   Quando você usar **Colar Acréscimo** ou **Colar Substituição**, os novos dados deverão conter exatamente o mesmo número de colunas dos dados originais. De preferência, as colunas de dados coladas ou anexadas também deverão ser dos mesmos tipos de dados ou compatíveis com os da tabela de destino. Em alguns casos, você pode usar um tipo de dados diferente, mas um erro **Tipos incompatíveis** poderá ser exibido.  
  
##  <a name="bkmk_paste_data"></a> Colar dados  
  
#### <a name="to-paste-data-into-the-designer"></a>Para colar dados na janela do designer  
  
-   No [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], clique no menu **Editar** e clique em um dos seguintes:  
  
    -   Clique em **Colar** para colar o conteúdo da Área de Transferência em uma nova tabela.  
  
    -   Clique em **Colar Acréscimo** para colar o conteúdo da Área de Transferência como linhas adicionais na tabela selecionada. As novas linhas serão adicionadas ao final da tabela.  
  
    -   Clique em **Colar Substituição** para substituir a tabela selecionada pelo conteúdo da Área de Transferência. Todos os nomes de cabeçalho de coluna existentes permanecerão na tabela e as relações serão preservadas.  
  
##  <a name="bkmk_paste_preview"></a> Caixa de diálogo Colar Visualização  
 A caixa de diálogo **Visualização de Colagem** o habilita a visualizar os dados copiados na janela do designer e a verificar se os dados foram copiados corretamente. Para acessar essa caixa de diálogo, copie os dados baseados em tabela no formato HTML para a área de transferência e, no designer, clique no menu **Editar** , clique em **Colar**, **Colar Acréscimo**ou **Colar Substituição**. As opções **Colar Acréscimo** e **Colar Substituição** só estarão disponíveis quando você adicionar ou substituir dados em uma tabela criada por meio de cópia e colagem da Área de Transferência. Não é possível usar **Colar Acréscimo** ou **Colar Substituição** para adicionar dados em uma tabela de dados importados.  
  
 As opções desta caixa de diálogo são diferentes, dependendo de você colar os dados em uma tabela completamente nova, colar os dados em uma tabela existente e, em seguida, substituir os dados existentes pelos novos, ou anexar os dados a uma tabela existente.  
  
### <a name="paste-to-new-table"></a>Colar em Nova Tabela  
 **Nome da tabela**  
 Especifique o nome da tabela que será criada no designer.  
  
 **Dados a Serem Colados**  
 Mostra um exemplo do conteúdo da Área de Transferência que será adicionado à tabela de destino.  
  
### <a name="paste-append"></a>Colar Acréscimo  
 **Dados existentes na tabela**  
 Mostra um exemplo dos dados existentes na tabela, para que você possa verificar as colunas, os tipos de dados etc.  
  
 **Dados a Serem Colados**  
 Mostra um exemplo do conteúdo da Área de Transferência. Os dados existentes serão adicionados por estes dados.  
  
### <a name="paste-replace"></a>Colar Substituição  
 **Dados existentes na tabela**  
 Mostra um exemplo dos dados existentes na tabela, para que você possa verificar as colunas, os tipos de dados etc.  
  
 **Dados a Serem Colados**  
 Mostra um exemplo do conteúdo da Área de Transferência. Os dados existentes na tabela de destino serão excluídos e as novas linhas serão inseridas na tabela.  
  
## <a name="see-also"></a>Consulte também  
 [Importar dados &#40;SSAS de Tabela&#41;](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [Fontes de dados com suporte &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)   
 [Definir o tipo de dados de uma coluna &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)  
  
  