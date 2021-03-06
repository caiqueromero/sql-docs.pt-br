---
title: Propriedade Filter | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Filter
helpviewer_keywords:
- Filter property
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9dc176d7c64d1845ddb863cd58fd41313967ccce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="filter-property"></a>Propriedade de filtro
Indica um filtro de dados em um [registros](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Configurações e valores de retorno

Define ou retorna um **Variant** valor, que pode conter um dos seguintes itens:  
  
-   **Cadeia de caracteres de critérios:** uma cadeia de caracteres composta de uma ou mais cláusulas individuais concatenadas com **AND** ou **OR** operadores.  
  
-   **Matriz de indicadores:** esse ponto de registros em valores de uma matriz de indicador exclusivo a **registros** objeto.  
  
-   Um [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) valor.  
  
## <a name="remarks"></a>Remarks

Use o **filtro** propriedade seletivamente retire registros em um **registros** objeto. Filtradas **registros** torna-se o cursor atual. Outras propriedades que retornam valores com base na atual **cursor** são afetados, como [propriedade AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md), [AbsolutePage Property (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md), [ Propriedade RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md), e [propriedade PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md). Definindo o **filtro** propriedade para um novo valor específico move o registro atual para o primeiro registro que satisfaz o novo valor.
  
A cadeia de caracteres de critérios é composta por cláusulas no formulário *valor de operador FieldName* (por exemplo, `"LastName = 'Smith'"`). Você pode criar cláusulas compostas concatenando cláusulas individuais com **AND** (por exemplo, `"LastName = 'Smith' AND FirstName = 'John'"`) ou **OR** (por exemplo, `"LastName = 'Smith' OR LastName = 'Jones'"`). Cadeias de caracteres de critérios, Use as seguintes diretrizes:

-   *FieldName* deve ser um nome de campo válido do **registros**. Se o nome do campo contiver espaços, você deve colocar o nome entre colchetes.  
  
-   Operador deve ser um dos seguintes: \<, >, \<=, > =, <>, =, ou **como**.  
  
-   É o valor com o qual você irá comparar os valores de campo (por exemplo, 'Smith', 24/8/95 #, 12.345 ou r $50,00). Use aspas simples com cadeias de caracteres e sinais sustenido (#) com datas. Para números, você pode usar a notação científica, cifrões e pontos decimais. Se o operador é **como**, valor pode usar curingas. São permitidas apenas o asterisco (*) e curingas de sinal de porcentagem (%) e devem ser o último caractere na cadeia de caracteres. Valor não pode ser nulo.  
  
> [!NOTE]
>  Para incluir aspas simples (') no filtro de valor, use duas aspas simples para representar um. Por exemplo, para filtrar o ' Malley, a cadeia de caracteres deve ser `"col1 = 'O''Malley'"`. Para incluir aspas simples no início e final do valor do filtro, coloque a cadeia de caracteres com sinais sustenido (#). Por exemplo, para filtrar '1', a cadeia de caracteres deve ser `"col1 = #'1'#"`.  
  
-   Não há nenhum precedência entre e e ou. As cláusulas podem ser agrupadas dentro dos parênteses. No entanto, você não pode agrupar cláusulas unidas por uma ou e, em seguida, ingressar no grupo para outra cláusula com um AND, como no seguinte trecho de código:  
 `(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   Em vez disso, você poderia construir esse filtro como  
 `(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   Em um **como** cláusula, você pode usar um caractere curinga no início e no final do padrão. Por exemplo, você pode usar `LastName Like '*mit*'`. Ou com **como** você pode usar um caractere curinga somente no final do padrão. Por exemplo, `LastName Like 'Smit*'`.  
  
 As constantes de filtro tornam mais fácil resolver conflitos de registro individuais durante o modo de atualização em lotes, permitindo que você exiba, por exemplo, somente os registros que foram afetados durante a última [método UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) chamada de método.  
  
Definindo o **filtro** propriedade em si pode falhar devido a um conflito com os dados subjacentes. Por exemplo, essa falha pode ocorrer quando um registro já foi excluído por outro usuário. Nesse caso, o provedor retornará avisos para o [coleção de erros (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md) coleção, mas não interromper a execução do programa. Um erro em tempo de execução ocorre somente se houver conflitos em todos os registros solicitados. Use o [(conjunto de registros ADO) a propriedade de Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) propriedade para localizar registros com conflitos.  
  
Definindo o **filtro** propriedade como uma cadeia de caracteres de comprimento zero ("") tem o mesmo efeito que usar o **adFilterNone** constante.
  
Sempre que o **filtro** propriedade for definida, a posição atual do registro move para o primeiro registro no subconjunto filtrado de registros a **registros**. Da mesma forma, quando o **filtro** propriedade estiver desmarcada, a posição atual do registro move para o primeiro registro o **registros**.

Suponha que um **registros** é filtrado com base em um campo de tipo variant, como o tipo sql_variant. Erro (DISP_E_TYPEMISMATCH ou 80020005) ocorre quando os subtipos dos valores de campo e o filtro usados na cadeia de caracteres de critérios não coincidem. Por exemplo, suponha que:

- Um **registros** objeto (rs) contém uma coluna (C) do tipo sql_variant.
- E um campo desta coluna foi atribuído um valor de 1 do tipo I4. A cadeia de caracteres é definida como `rs.Filter = "C='A'"` no campo.

Essa configuração gera o erro em tempo de execução. No entanto, `rs.Filter = "C=2"` aplicado no mesmo campo não produzirá um erro. E o campo é filtrado fora do conjunto de registros atual.

Consulte o [indicador Property (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md) propriedade para obter uma explicação dos valores de indicador do qual você pode criar uma matriz a ser usado com a propriedade de filtro.

Somente filtros na forma de cadeias de caracteres de critérios afetam o conteúdo de um persistente **registros**. Um exemplo de uma cadeia de caracteres de critérios é `OrderDate > '12/31/1999'`. Filtros criados com uma matriz de indicadores, ou usando um valor da **FilterGroupEnum**, não afetam o conteúdo de persistente **registros**. Essas regras se aplicam a conjuntos de registros criados com cursores do lado do cliente ou do servidor.
  
> [!NOTE]
>  Quando você aplica o sinalizador adFilterPendingRecords para um filtrado e modificado **registros** no modo de atualização em lotes, o resultante **registros** está vazio se a filtragem se baseia o campo de chave de um tabela de chave única e a modificação foi feita nos valores de campo de chave. O RSoP **registros** serão não-vazia se uma das instruções a seguir for verdadeira:  
  
-   A filtragem foi baseada em campos de não-chave em uma tabela de chave única.  
  
-   A filtragem foi baseada em todos os campos em uma tabela com chave vários.  
  
-   As modificações feitas nos campos de não-chave em uma tabela de chave única.  
  
-   As modificações feitas em todos os campos em uma tabela com chave vários.  
  
A tabela a seguir resume os efeitos de **adFilterPendingRecords** em combinações diferentes de filtragem e modificações. A coluna esquerda mostra as modificações possíveis. As modificações podem ser feitas em qualquer um dos campos sem chave, o campo de chave em uma tabela de chave única, ou em qualquer um dos campos de chave em uma tabela com chave vários. A linha superior mostra o critério de filtragem. A filtragem pode se basear em qualquer um dos campos sem chave, o campo de chave em uma tabela de chave única, ou qualquer um dos campos de chave em uma tabela com chave vários. As células de interseção mostram os resultados. Um **+** sinal significa que se aplicam **adFilterPendingRecords** resulta em não-vazia **registros**. Um **-** sinal significa vazio **registros**.  
  
||Não chaves|Chave única|Várias chaves|
|-|--------------|----------------|-------------------|
|**Não chaves**|+|+|+|
|**Chave única**|+|-|N/A|
|**Várias chaves**|+|N/A|+|
|||||
  
## <a name="applies-to"></a>Aplica-se a

[Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Consulte também

[Exemplo de propriedades de RecordCount (VB) e filtro](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)
[filtro e exemplo de propriedades de RecordCount (VC + +)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)
[(ADO) do método Clear](../../../ado/reference/ado-api/clear-method-ado.md) 
 [Otimizar propriedade dinâmica (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)
