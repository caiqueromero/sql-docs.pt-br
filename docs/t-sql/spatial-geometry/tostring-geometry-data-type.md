---
title: ToString (tipo de dados geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ToString (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6a5c6ecab0e05255f6dd1a798478e081c83cd4a5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="tostring-geometry-data-type"></a>ToString (tipo de dados geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retorna a representação WKT (Well-Known Text) do OGC (Open Geospatial Consortium) de uma instância geométrica, aumentada com qualquer valor Z (elevação) e M (medida) presente na instância.
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 Tipo de retorno do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **nvarchar(max)**  
  
 Tipo de retorno do CLR: **SqlString**  
  
## <a name="remarks"></a>Remarks  
 Esse método retornará a cadeia de caracteres "Nulo" quando chamado em instâncias nulas.  
  
 Em instâncias não nulas, esse método é equivalente a usar `AsTextZM().`  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir cria uma instância de `LineString` e usa `ToString()` para buscar a descrição de texto da instância.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Consulte Também  
 [STAsText &#40;tipo de dados geometry&#41;](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [Métodos estendidos em instâncias geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

