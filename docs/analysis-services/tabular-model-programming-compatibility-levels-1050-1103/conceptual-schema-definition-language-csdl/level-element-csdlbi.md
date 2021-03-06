---
title: Nível de elemento (CSDLBI) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 76fc2e9f2f6aa20c7c18a43e7b88df8d24e9d13b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="level-element-csdlbi"></a>Elemento Level (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  O elemento Level é um tipo complexo que define um único nível em uma hierarquia  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 A tabela a seguir lista os elementos e atributos que definem o elemento Level.  
  
|Nome|É obrigatório|Descrição|  
|----------|-----------------|-----------------|  
|Origem|Sim|Um contêiner para a referência da propriedade.|  
|PropertyRef|Sim|Uma referência a uma propriedade da instância. Outros atributos do nível, como legendas, nome e nome de referência, podem ser tirados da propriedade da instância referenciada. Nesse caso, você não precisa especificá-los no elemento Level.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre hierarquias em modelos tabulares, consulte [Elemento Hierarchy &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).  
  
## <a name="example"></a>Exemplo  
 **Tabela**  
  
 O exemplo a seguir, na versão 1.1 da CSDLBI, mostra a definição de vários níveis em uma hierarquia do exemplo de modelo de tabela da AdventureWorks.  
  
```  
  
<bi:Hierarchy Name="Category">  
   <bi:Level Name="CategoryName">  
     <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
     </bi:Source>  
   </bi:Level>  
   <bi:Level Name="ProductName">  
     <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
     </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="example"></a>Exemplo  
 **Multidimensional**  
  
 O exemplo a seguir, na versão 1.1 da CSDLBI, mostra uma hierarquia com vários níveis do cubo Operações da Contoso.  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
     <bi:Documentation>  
        <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
     </bi:Documentation>  
  
     <bi:Level Name="ProductLine">  
        <bi:Source>  
        <bi:PropertyRef Name="ProductLine" />  
        </bi:Source>  
     </bi:Level>  
  
     <bi:Level Name="ModelName">  
        <bi:Source>  
        <bi:PropertyRef Name="ModelName" />  
        </bi:Source>  
     </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas sobre o modelo de objeto de tabela em compatibilidade 1050 1103 por meio de níveis](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Compreendendo funções para hierarquias pai-filho em DAX](http://msdn.microsoft.com/en-us/b11f0cff-cee4-4ae7-a5b3-ebe288fc42d3)   
 [Configurar o & #40; Todos os & #41; Nível para hierarquias de atributo](../../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
