---
title: sys. selective_xml_index_paths (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_schema_attributes_TSQL
- xml_schema_attributes
- sys.xml_schema_attributes_TSQL
- sys.xml_schema_attributes
dev_langs: TSQL
helpviewer_keywords: sys.xml_schema_attributes catalog view
ms.assetid: 07a73d71-ec3e-4894-947a-5859ca62c606
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6c2f8156f9821bb6d4d0f70ae1af200a33ce3cb9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sysselectivexmlindexpaths-transact-sql"></a>sys.selective_xml_index_paths (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Disponível a partir do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1, cada linha de sys.selective_xml_index_paths representa um caminho promovido de um índice xml seletivo específico.  
  
 Se você criar um índice xml seletivo no xmlcol da tabela T usando a seguinte instrução,  
  
```  
CREATE SELECTIVE XML INDEX sxi1 ON T(xmlcol)   
FOR ( path1 = '/a/b/c' AS XQUERY 'xs:string',  
      path2 = '/a/b/d' AS XQUERY 'xs:double'  
    )  
```  
  
 Haverá duas novas linhas em sys.selective_xml_index_paths correspondente ao índice sxi1.  

  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID da tabela com coluna XML.|  
|**index_id**|**int**|ID exclusiva do índice xml seletivo.|  
|**path_id**|**int**|ID do caminho XML promovido.|  
|**caminho**|**nvarchar(4000)**|Caminho promovido. Por exemplo, '/a/b/c/d/e'.|  
|**name**|**sysname**|Nome do caminho.|  
|**path_type**|**tinyint**|0 = XQUERY<br /><br /> 1 = SQL|  
|**path_type_desc**|**sysname**|Com base em **path_type** valor 'XQUERY' ou 'SQL'.|  
|**xml_component_id**|**int**|ID exclusiva do componente de esquema XML no banco de dados.|  
|**xquery_type_description**|**nvarchar(4000)**|Nome do tipo xsd especificado.|  
|**is_xquery_type_inferred**|**bit**|1 = o tipo é inferido.|  
|**xquery_max_length**|**smallint**|Comprimento máximo (em caracteres do tipo xsd).|  
|**is_xquery_max_length_inferred**|**bit**|1 = o comprimento máximo é inferido.|  
|**is_node**|**bit**|0 = dica node() ausente.<br /><br /> 1 = dica de otimização node() aplicada.|  
|**system_type_id**|**tinyint**|ID de coluna do tipo de sistema.|  
|**user_type_id**|**tinyint**|ID do tipo de usuário da coluna.|  
|**max_length**|**smallint**|Comprimento máximo (em bytes) do tipo.<br /><br /> -1 = O tipo de dados de coluna é varchar(max), nvarchar(max), varbinary(max) ou xml.|  
|**precisão**|**tinyint**|Precisão máxima do tipo se for numérico. Caso contrário, 0.|  
|**escala**|**tinyint**|Escala máxima do tipo se for numérico. Caso contrário, será 0.|  
|**collation_name**|**sysname**|Nome do agrupamento do tipo se baseado em caractere. Caso contrário, NULL.|  
|**is_singleton**|**bit**|0 = dica SINGLETON ausente.<br /><br /> 1 = dica de otimização SINGLETON aplicada.|  
  
## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obter mais informações, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exibições de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Esquemas XML &#40; Sistema de tipo XML &#41; Exibições de catálogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  