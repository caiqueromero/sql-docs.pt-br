---
title: Novos recursos de data e hora com versões anteriores do SQL Server (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 96976bac-018c-47cc-b1b2-fa9605eb55e5
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5cb50889a9cb584e5f22d5f2e77960dba567fda1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>Novos recursos de data e hora com versões anteriores do SQL Server (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Este tópico descreve o comportamento esperado quando um aplicativo cliente que usa recursos aprimorados de data e hora se comunica com uma versão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anteriores [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]e quando um cliente compilado com uma versão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client anteriores [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] envia comandos para um servidor que oferece suporte a recursos avançados de data e hora.  
  
## <a name="down-level-client-behavior"></a>Comportamento do cliente de versão anterior  
 Aplicativos cliente que usam uma versão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client anterior ao [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ver os tipos de data/hora novo como **nvarchar** colunas. O conteúdo de coluna são representações literais. Para obter mais informações, consulte a seção "Formatos de dados: cadeias e literais" [suporte de tipo de dados para aprimoramentos de hora e data do OLE DB](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md). O tamanho da coluna é o comprimento de literal máximo para a precisão especificada para a coluna.  
  
 APIs de catálogo retornarão metadados consistentes com o código de tipo de dados de versão anterior retornado ao cliente (por exemplo, **nvarchar**) e a representação de nível inferior (por exemplo, o formato de literal apropriado) associada. Entretanto, o nome do tipo de dados retornado será o nome de tipo [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] real.  
  
 Quando um aplicativo cliente de nível inferior é executada em relação a um [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou posterior) no qual as alterações de esquema de data/hora foram feitas tipos de servidor, o comportamento esperado é o seguinte:  
  
|Tipo de cliente OLE DB|Tipo SQL Server 2005|Tipo de 2008 (ou posterior) SQL Server|Conversão de resultado (servidor para cliente)|Conversão de parâmetro (cliente para servidor)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|Datetime|Data|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Campos de hora definidos como zero.|IRowsetChange falhará devido ao truncamento de cadeia de caracteres se o campo de hora for diferente de zero.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Campos de data definidos como a data atual.|IRowsetChange falhará devido ao truncamento de cadeia de caracteres se frações de segundo forem diferentes de zero.<br /><br /> A data é ignorada.|  
|DBTYPE_DBTIME||Time(7)|Falha – literal de hora inválido.|OK|  
|DBTYPE_DBTIMESTAMP|||Falha – literal de hora inválido.|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2(3)|OK|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2 (7)|OK|OK|  
|DBTYPE_DBDATE|Smalldatetime|Data|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Campos de hora definidos como zero.|IRowsetChange falhará devido ao truncamento de cadeia de caracteres se o campo de hora for diferente de zero.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Campos de data definidos como a data atual.|IRowsetChange falhará devido ao truncamento de cadeia de caracteres se frações de segundo forem diferentes de zero.<br /><br /> A data é ignorada.|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|OK|OK|  
  
 OK quer dizer que se funcionou com o [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], deveria continuar funcionando com o [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou posterior).  
  
 Só as seguintes alterações de esquema comuns foram consideradas:  
  
-   Usar um novo tipo em que logicamente um aplicativo exige somente um valor de data ou hora. No entanto, o aplicativo foi forçado a usar **datetime** ou **smalldatetime** porque tipos separados de data e hora não estavam disponíveis.  
  
-   Usar um novo tipo para obter precisão ou exatidão adicional de frações de segundos.  
  
-   Alternar para **datetime2** porque esse é o tipo de dados preferencial para data e hora.  
  
 Aplicativos que usam metadados do servidor obtidos por meio de conjuntos de linhas de esquema ou ICommandWithParameters:: Getparameterinfo para definir informações de tipo de parâmetro por meio de ICommandWithParameters:: SetParameterInfo falharão durante conversões de cliente em que a cadeia de caracteres representação de um tipo de origem é maior que a representação de cadeia de caracteres do tipo de destino. Por exemplo, se uma associação de cliente usa DBTYPE_DBTIMESTAMP e a coluna de servidor de data, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client converterá o valor para "hh:mm:ss.fff mm-dd-aaaa", mas os metadados do servidor serão retornados como **nvarchar (10)**. O estouro resultante causa DBSTATUS_E_CATCONVERTVALUE. Problemas semelhantes ocorrem com conversões de dados por IRowsetChange, porque os metadados do conjunto de linhas é definido de metadados do conjunto de resultados.  
  
### <a name="parameter-and-rowset-metadata"></a>Parâmetro e metadados de conjunto de linhas  
 Esta seção descreve os metadados para parâmetros, colunas de resultados e conjuntos de linhas de esquema para clientes que são compilados com uma versão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client anterior ao [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 A estrutura DBPARAMINFO retorna as informações a seguir por meio de *prgParamInfo* parâmetro:  
  
|Tipo de parâmetro|wType|ulParamSize|bPrecision|bScale|  
|--------------------|-----------|-----------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
 Note que alguns destes intervalos de valor não são contínuos; por exemplo, 9 está faltando em 8,10..16. Isso se deve à adição de um ponto decimal quando a precisão fracionária é maior que zero.  
  
#### <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 As seguintes colunas são retornadas:  
  
|Tipo de coluna|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|  
|-----------------|--------------------|--------------------------|-------------------------|--------------------------------------------------|  
|date|DBTYPE_WSTR|10|NULL|NULL|  
|time|DBTYPE_WSTR|8, 10..16|NULL|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 A estrutura de DBCOLUMNINFO retorna as seguintes informações:  
  
|Tipo de parâmetro|wType|ulColumnSize|bPrecision|bScale|  
|--------------------|-----------|------------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
### <a name="schema-rowsets"></a>Conjuntos de linhas de esquema  
 Esta seção aborda metadados para parâmetros, colunas de resultados e conjuntos de linhas de esquema para novos tipos de dados. Essa informação é útil se você tiver um provedor de cliente desenvolvido usando ferramentas anteriores [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
#### <a name="columns-rowset"></a>Conjunto de linhas de COLUMNS  
 Os valores de coluna a seguir são retornados para tipos de data/hora:  
  
|Tipo de coluna|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|date|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|datetime|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|NULL|  
  
#### <a name="procedureparameters-rowset"></a>Conjunto de linhas de PROCEDURE_PARAMETERS  
 Os valores de coluna a seguir são retornados para tipos de data/hora:  
  
|Tipo de coluna|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|date|DBTYPE_WSTR|10|20|date|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|datetime|DBTYPE_DBTIMESTAMP|NULL|NULL|datetime|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|datetimeoffset|  
  
#### <a name="providertypes-rowset"></a>Conjunto de linhas de PROVIDER_TYPES  
 As linhas a seguir são retornadas para tipos de data/hora:  
  
|Tipo -><br /><br /> Coluna|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_WSTR|DBTYPE_WSTR|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_WSTR|DBTYPE_WSTR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|‘|‘|‘|‘|‘|‘|  
|LITERAL_SUFFIX|‘|‘|‘|‘|‘|‘|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_TRUE|VARIANT_FALSE|VARIANT_FALSE|  
|IS_FIXEDLENGTH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
  
## <a name="down-level-server-behavior"></a>Comportamento de servidor de versão anterior  
 Quando conectado a um servidor de uma versão anterior ao [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], qualquer tentativa de usar os novos nomes de tipo de servidor (por exemplo, com ICommandWithParameters:: SetParameterInfo ou itabledefinition:: CreateTable) resultará em DB_E_BADTYPENAME.  
  
 Se novos tipos forem associados para parâmetros ou resultados sem o uso de um nome de tipo, e o novo tipo for usado para especificar o tipo de servidor implicitamente ou se não houver nenhuma conversão válida do tipo de servidor no tipo de cliente, DB_E_ERRORSOCCURRED será retornado e DBBINDSTATUS_UNSUPPORTED_CONVERSION será definido como o status de associação para o acessador usado em Execute.  
  
 Se houver uma conversão de cliente aceita do tipo de buffer no tipo de servidor para a versão do servidor na conexão, todos os tipos de buffer do cliente poderão ser usados. Nesse contexto, *tipo de servidor* significa que o tipo especificado pelo ICommandWithParameters:: SetParameterInfo ou implícita por tipo de buffer se ICommandWithParameters:: SetParameterInfo não foi chamado. Isto significa que DBTYPE_DBTIME2 e DBTYPE_DBTIMESTAMPOFFSET poderão ser usados com servidores de versões anteriores ou quando DataTypeCompatibility=80, se a conversão de cliente em um tipo de servidor aceito for bem-sucedida. Obviamente, se o tipo de servidor estiver correto, um erro ainda poderá ser relatado pelo servidor se ele não puder executar uma conversão implícita no tipo de servidor real.  
  
## <a name="sspropinitdatatypecompatibility-behavior"></a>Comportamento de SSPROP_INIT_DATATYPECOMPATIBILITY  
 Quando SSPROP_INIT_DATATYPECOMPATIBILITY for definido como SSPROPVAL_DATATYPECOMPATIBILITY_SQL2000, os tipos de data/hora novo e metadados associados aparecem para os clientes como eles aparecem para clientes de nível inferior, conforme descrito em [a alterações de cópia em massa Avançado tipos de data e hora &#40;OLE DB e ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
## <a name="comparability-for-irowsetfind"></a>Comparações de IRowsetFind  
 Todos os operadores de comparação são permitidos para os novos tipos de data/hora, porque eles aparecem como tipos de cadeia de caracteres, em vez de tipos de data/hora.  
  
## <a name="see-also"></a>Consulte também  
 [Data e hora melhorias & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
