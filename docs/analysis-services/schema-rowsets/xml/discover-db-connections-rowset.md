---
title: Conjunto de linhas DISCOVER_DB_CONNECTIONS | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3680b130dabcb13d6b9a518e54389aa13be441eb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="discoverdbconnections-rowset"></a>Conjunto de linhas DISCOVER_DB_CONNECTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Oferece uso de recursos e de informações de atividade sobre as conexões abertas no momento do servidor para um banco de dados.  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas **DISCOVER_DB_CONNECTIONS** contém as colunas a seguir.  
  
|Nome da coluna|Indicador de tipo|Comprimento|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CONNECTION_CATALOG_NAME**|**DBTYPE_WSTR**||O nome do banco de dados conectado no momento.|  
|**CONNECTION_ID**|**DBTYPE_I4**||Um número exclusivo que identifica a conexão.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**||O tempo ocioso, em milissegundos, desde o início da conexão.|  
|**CONNECTION_IN_USE**|**DBTYPE_I4**||indica se a conexão está ativa (1) ou ociosa (0).|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||A data e a hora UTC do servidor quando a execução do último comando foi concluída.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||A data e a hora UTC do servidor quando a execução do último comando foi iniciada.|  
|**CONNECTION_SERVER_NAME**|**DBTYPE_WSTR**||O nome do servidor conectado no momento.|  
|**CONNECTION_SPID**|**DBTYPE_I4**||A ID da sessão.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||A data e a hora UTC do servidor quando a conexão foi iniciada.|  
|**CONNECTION_USAGE_TIME_MS**|**DBTYPE_I8**||O tempo de atividade da conexão, em milissegundos, desde o início da conexão.|  
  
 Este conjunto de linhas do esquema não é classificado.  
  
> [!IMPORTANT]  
>  O conjunto de linhas **DISCOVER_DB_CONNECTIONS** só exibirá informações quando o serviço estiver conectado às fontes de dados relacionais.  
  
## <a name="restriction-columns"></a>Colunas de restrição  
 O conjunto de linhas **DISCOVER_DB_CONNECTIONS** pode ser restringido nas colunas listadas na tabela a seguir.  
  
|Nome da coluna|Indicador de tipo|Estado de restrição|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Opcional.|  
|CONNECTION_IN_USE|DBTYPE_I4|Opcional.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Opcional.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Obrigatórios.|  
|CONNECTION_SPID|DBTYPE_I4|Opcional.|  
  
## <a name="see-also"></a>Consulte também  
 [XML for Analysis conjuntos de linhas de esquema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
