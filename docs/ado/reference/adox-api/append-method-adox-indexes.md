---
title: Método (ADOX índices) append | Microsoft Docs
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
apitype: COM
f1_keywords:
- Indexes::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b25f75f89181f2020238f3a113b7a9908c6a88d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-adox-indexes"></a>Método (ADOX índices) append
Adiciona um novo [índice](../../../ado/reference/adox-api/index-object-adox.md) o objeto para o [índices](../../../ado/reference/adox-api/indexes-collection-adox.md) coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *Index*  
 O **índice** objeto a ser acrescentado ou o nome do índice para criar e anexar.  
  
 *Colunas*  
 Opcional. Um **Variant** valor que especifica os nomes das colunas a serem indexados. O *colunas* parâmetro corresponde para os valores da [nome](../../../ado/reference/adox-api/name-property-adox.md) propriedade de um [coluna](../../../ado/reference/adox-api/column-object-adox.md) objeto ou objetos.  
  
## <a name="remarks"></a>Remarks  
 O *colunas* parâmetro pode ser o nome de uma coluna ou uma matriz de nomes de coluna.  
  
 Se o provedor não oferece suporte a criação de índices, ocorrerá um erro.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Coleção Indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>Consulte também  
 [Índices de acrescentar o exemplo de método (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Acrescente o método (ADOX colunas)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [(Grupos de ADOX) do método append](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [(ADOX chaves) do método append](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Acrescente o método (ADOX procedimentos)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [(Tabelas ADOX) do método append](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Acrescente o método (ADOX usuários)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Método Append (Exibições do ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
