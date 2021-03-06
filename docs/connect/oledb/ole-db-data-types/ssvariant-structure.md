---
title: Estrutura SSVARIANT | Microsoft Docs
description: Estrutura SSVARIANT no OLE DB Driver para SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: eb977dbe9ef7bed4e6c98ef612bd6e2bb67bf159
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ssvariant-structure"></a>Estrutura SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  O **SSVARIANT** estrutura, que é definida em msoledbsql.h, corresponde a um valor DBTYPE_SQLVARIANT no Driver OLE DB para SQL Server.  
  
 **SSVARIANT** é uma união distinta. Dependendo do valor do membro vt, o consumidor pode determinar qual membro deve ser lido. os valores VT correspondem aos [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipos de dados. Portanto, o **SSVARIANT** estrutura pode conter qualquer tipo de SQL Server. Para obter mais informações sobre a estrutura de dados para tipos de OLE DB padrão, consulte [indicadores de tipo](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Remarks  
 Quando DataTypeCompat = = 80, vários **SSVARIANT** subtipos se tornam cadeias de caracteres. Por exemplo, os valores vt seguintes aparecerão em **SSVARIANT** como VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Quando DateTypeCompat == 0, estes tipos aparecerão no seu formulário nativo.  
  
 Para obter mais informações sobre SSPROP_INIT_DATATYPECOMPATIBILITY, consulte [usando Conexão String Keywords com OLE DB para SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 O arquivo msoledbsql.h contém macros de acesso variantes que simplificam a referência os tipos de membro no **SSVARIANT** estrutura. Um exemplo é V_SS_DATETIMEOFFSET que você pode usar da seguinte maneira:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Para o conjunto completo de macros de acesso para cada membro do **SSVARIANT** estrutura, consulte o arquivo msoledbsql.h.  
  
 A tabela a seguir descreve os membros do **SSVARIANT** estrutura:  
  
|Membro|Indicador de tipo OLE DB|Tipo de dados OLE DB C|valor vt|Comentários|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Especifica o tipo de valor contido no **SSVARIANT** struct.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Oferece suporte a **tinyint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|sShortIntVal|DBTYPE_I2|**CURTO**|**VT_SS_I2**|Oferece suporte a **smallint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|lIntVal|DBTYPE_I4|**LONGAS**|**VT_SS_I4**|Oferece suporte a **int** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Oferece suporte a **bigint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Oferece suporte a **real** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Oferece suporte a **float** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Oferece suporte a **money** e **smallmoney** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipos de dados.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Oferece suporte a **bit** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Oferece suporte a **uniqueidentifier** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Oferece suporte a **numérico** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Oferece suporte a **data** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Oferece suporte a **smalldatetime**, **datetime**, e **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipos de dados.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Oferece suporte a **tempo** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.<br /><br /> Inclui os seguintes membros:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**bytes**) Especifica a escala de *tTime2Val* valor.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Oferece suporte a **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.<br /><br /> Inclui os seguintes membros:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**bytes**) Especifica a escala de *tsDataTimeVal* valor.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Oferece suporte a **datetimeoffset** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de dados.<br /><br /> Inclui os seguintes membros:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**bytes**) Especifica a escala de *tsoDateTimeOffsetVal* valor.|  
|NCharVal|Não existe um indicador de tipo OLE DB correspondente.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Oferece suporte a **nchar** e **nvarchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipos de dados.<br /><br /> Inclui os seguintes membros:<br /><br /> *sActualLength* (**CURTO**) Especifica o comprimento real para a cadeia de caracteres para o qual *pwchNCharVal* pontos. Não inclui o zero final.<br /><br /> *sMaxLength* (**CURTO**) Especifica o comprimento máximo para a cadeia de caracteres para o qual *pwchNCharVal* pontos.<br /><br /> *pwchNCharVal* (**WCHAR** \*) ponteiro para a cadeia de caracteres.<br /><br /> Membros não usados: *rgbReserved*, *dwReserved*, e *pwchReserved*.|  
|CharVal|Não existe um indicador de tipo OLE DB correspondente.|**estrutura _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Oferece suporte a **char** e **varchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipos de dados.<br /><br /> Inclui os seguintes membros:<br /><br /> *sActualLength* (**CURTO**) Especifica o comprimento real para a cadeia de caracteres para o qual *pchCharVal* pontos. Não inclui o zero final.<br /><br /> *sMaxLength* (**CURTO**) Especifica o comprimento máximo para a cadeia de caracteres para o qual *pchCharVal* pontos.<br /><br /> *pchCharVal* (**CHAR** \*) ponteiro para a cadeia de caracteres.<br /><br /> Membros não usados:<br /><br /> *rgbReserved*, *dwReserved*, e *pwchReserved*.|  
|BinaryVal|Não existe um indicador de tipo OLE DB correspondente.|**estrutura _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Oferece suporte a **binário** e **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipos de dados.<br /><br /> Inclui os seguintes membros:<br /><br /> *sActualLength* (**CURTO**) Especifica o comprimento real dos dados para o qual *prgbBinaryVal* pontos.<br /><br /> *sMaxLength* (**CURTO**) Especifica o comprimento máximo para os dados para o qual *prgbBinaryVal* pontos.<br /><br /> *prgbBinaryVal* (**bytes** \*) ponteiro para os dados binários.<br /><br /> Membro não usado: *dwReserved*.|  
|UnknownType|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados & #40; OLE DB & #41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
