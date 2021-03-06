---
title: Controle de alterações na tabela de Base do conjunto de registros (ADO) | Microsoft Docs
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
helpviewer_keywords:
- Unique Table property [ADO]
- Unique Schema property [ADO]
- Unique Catalog property [ADO]
ms.assetid: d0e775d8-e353-46a1-ad10-ed4cc240dfaa
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76bf7ee2916e6fa4277154d7261f40b9b5959ea9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Tabela exclusiva, de esquema exclusivo exclusiva catálogo propriedades dinâmica (ADO)
Permite que você atentamente as modificações de controle para uma tabela base específica em um [registros](../../../ado/reference/ado-api/recordset-object-ado.md) que foi formado por uma operação de junção em várias tabelas base.  
  
-   **Tabela exclusiva** Especifica o nome da tabela base na qual as atualizações, inserções e exclusões são permitidas.  
  
-   **Esquema exclusivo** Especifica o *esquema*, ou o nome do proprietário da tabela.  
  
-   **Catálogo exclusivo** Especifica o *catálogo*, ou o nome do banco de dados que contém a tabela.  
  
## <a name="settings-and-return-values"></a>Configurações e valores de retorno  
 Define ou retorna um **cadeia de caracteres** valor que é o nome da tabela, esquema ou catálogo.  
  
## <a name="remarks"></a>Remarks  
 A tabela base desejada é identificada exclusivamente por seus nomes de tabela, esquema e catálogo. Quando o **tabela exclusiva** propriedade for definida, os valores da **esquema exclusivo** ou **catálogo exclusivo** propriedades são usadas para localizar a tabela base. É pretendido, mas não obrigatório, que um ou ambos o **esquema exclusivo** e **catálogo exclusivo** propriedades ser definida antes do **tabela exclusiva** está definida.  
  
 A chave primária do **tabela exclusiva** é tratado como a chave primária de todo o **registros**. Esta é a chave usada para qualquer método que exigem uma chave primária.  
  
 Enquanto **tabela exclusiva** for definida, o [excluir](../../../ado/reference/ado-api/delete-method-ado-recordset.md) método afeta apenas a tabela nomeada. O [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [atualização](../../../ado/reference/ado-api/update-method.md), e [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) métodos afetam quaisquer tabelas base subjacentes de apropriada da **Registros**.  
  
 **Tabela exclusiva** deve ser especificado antes de fazer qualquer ressincronizações personalizadas. Se **tabela exclusiva** não foi especificado, o [comando Resync](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) propriedade não terá efeito.  
  
 Um erro de tempo de execução resulta se uma tabela base exclusiva não pode ser encontrada.  
  
 Essas propriedades dinâmicas são acrescentadas ao **registros** objeto [propriedades](../../../ado/reference/ado-api/properties-collection-ado.md) coleção quando o [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) está definida como  **adUseClient**.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
