---
title: Colunas de estrutura de mineração | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1cbdcd14127cdf45eb35dd7a24652be4f7c4d613
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="mining-structure-columns"></a>Colunas da estrutura de mineração
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Você define as colunas em uma estrutura de mineração quando cria a estrutura de mineração, escolhendo colunas de dados externos e especificando como os dados serão usados na modelagem. Portanto, colunas de estrutura de mineração são mais do que cópias de dados de uma fonte de dados: elas definem como os dados da fonte serão usados pelo modelo de mineração. Você pode atribuir propriedades que determinam como os dados são discretizados, propriedades que descrevem como os valores de dados são distribuídos  
  
 As colunas da estrutura de mineração são projetadas para serem flexíveis e extensíveis, porque cada algoritmo utilizado para criar um modelo de mineração pode utilizar diferentes colunas da estrutura para interpretar os dados. Em vez de ter um conjunto de dados para cada modelo, você pode usar uma única estrutura de mineração e usar as colunas dela para personalizar os dados para cada modelo.  
  
## <a name="defining-mining-structure-columns"></a>Definindo colunas da estrutura de mineração  
 Os tipos de dados e de conteúdo básicos que definem as colunas da estrutura são derivados da fonte de dados utilizada para criar a estrutura. Você pode alterar essas configurações na estrutura de mineração e também definir os sinalizadores de modelagem bem como a distribuição das colunas contínuas.  
  
 A definição de uma coluna de estrutura de mineração deve conter as seguintes informações:  
  
-   **ID**: O nome exclusivo da coluna, que costuma ser igual ao nome. Isso não pode ser alterado após a criação da estrutura de mineração, mas o nome pode ser alterado.  
  
-   **Nome**: Um nome ou alias para a coluna.  
  
-   **Conteúdo**: Uma enumeração que descreve se os dados são discretos ou contínuos.  
  
-   **Tipo**: Uma enumeração que indica o tipo de dados geral.  
  
-   **Distribuição**: Uma enumeração que descreve a distribuição esperada de valores. A distribuição será incluída se a coluna for contínua.  
  
-   **Sinalizadores de modelagem**: Uma enumeração que indica como tratar valores ausentes e assim por diante. Sinalizadores de modelagem também podem ser definidos no modelo de mineração, mas os sinalizadores de modelo diferem dos sinalizadores usados em colunas de estrutura.  
  
-   **Associações**: Propriedades que especificam os dados de origem.  
  
 Os algoritmos de terceiros também podem incluir propriedades personalizadas que podem ser definidas na coluna da estrutura de mineração.  
  
 Para obter mais informações sobre a estrutura e o modelo de mineração de dados, consulte [Estruturas de Mineração &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
## <a name="related-content"></a>Conteúdo relacionado  
 Consulte os tópicos a seguir para obter mais informações sobre como definir e usar colunas da estrutura de mineração.  
  
|Tópico|Links|  
|-----------|-----------|  
|Descreve os tipos de dados que você pode utilizar para definir uma coluna da estrutura de mineração.|[Tipos de dados &#40;Mineração de dados&#41;](../../analysis-services/data-mining/data-types-data-mining.md)|  
|Descreve os tipos de conteúdo que estão disponíveis para cada tipo de dados contido em uma coluna de estrutura de mineração. Tipos de conteúdo são dependentes do tipo de dados. O tipo de conteúdo é atribuído ao nível de modelo e determina como os dados de coluna são usados pelo modelo.|[Tipos de conteúdo &#40;Data Mining&#41;](../../analysis-services/data-mining/content-types-data-mining.md)|  
|Apresenta o conceito de tabelas aninhadas e explica como tabelas aninhadas podem ser adicionadas à fonte de dados como colunas de estrutura de mineração.|[Colunas classificadas &#40;Mineração de dados&#41;](../../analysis-services/data-mining/classified-columns-data-mining.md)|  
|Lista e explica as propriedades de distribuição que você pode definir em uma coluna de estrutura de mineração para especificar a distribuição esperada de valores na coluna.|[Distribuições de colunas &#40;Mineração de dados&#41;](../../analysis-services/data-mining/column-distributions-data-mining.md)|  
|Explica o conceito de discretização (às vezes chamado de *compartimentalização*) e descreve os métodos que o Analysis Services fornece para discretizar dados numéricos contínuos.|[Métodos de discretização &#40;Mineração de dados&#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)|  
|Descreve os sinalizadores de modelagem que você pode definir em uma coluna da estrutura de mineração.|[Sinalizadores de modelagem &#40;Mineração de dados&#41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)|  
|Descreve as colunas classificadas, que são um tipo especial de coluna a ser usada para relacionar uma coluna da estrutura de mineração a outra.|[Colunas classificadas &#40;Mineração de dados&#41;](../../analysis-services/data-mining/classified-columns-data-mining.md)|  
|Saiba como adicionar e modificar colunas de estrutura de mineração.|[Tarefas e instruções da estrutura de mineração](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de mineração & #40; Analysis Services – mineração de dados & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Colunas do modelo de mineração](../../analysis-services/data-mining/mining-model-columns.md)  
  
  
