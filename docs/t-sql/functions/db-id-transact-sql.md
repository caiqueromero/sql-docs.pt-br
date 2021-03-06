---
title: DB_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DB_ID_TSQL
- DB_ID
dev_langs:
- TSQL
helpviewer_keywords:
- viewing database ID numbers
- IDs [SQL Server], databases
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
- displaying database ID numbers
- DB_ID function
ms.assetid: 7b3aef89-a6fd-4144-b468-bf87ebf381b8
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cb7e49f0ebd4746ccad1a9647ac2f35d61efcdc9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="dbid-transact-sql"></a>DB_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retorna o número de identificação (ID) do banco de dados.
  
![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxe  
  
```sql
DB_ID ( [ 'database_name' ] )   
```  
  
## <a name="arguments"></a>Argumentos  
'*database_name*'  
É o nome do banco de dados usado para retornar a ID do banco de dados correspondente. *database_name* é **sysname**. Se *database_name* for omitido, a ID de banco de dados atual será retornada.
  
## <a name="return-types"></a>Tipos de retorno
**int**
  
## <a name="permissions"></a>Permissões  
Se o chamador de **DB_ID** não for o proprietário do banco de dados e o banco de dados não for o **master** nem **tempdb**, as permissões mínimas necessárias para ver a linha correspondente serão as permissões no nível do servidor ALTER ANY DATABASE ou VIEW ANY DATABASE ou a permissão CREATE DATABASE no banco de dados **master**. O banco de dados ao qual o chamador está conectado sempre pode ser exibido em **sys.databases**.
  
> [!IMPORTANT]  
>  Por padrão, a função pública tem a permissão VIEW ANY DATABASE, permitindo que todos os logons vejam informações do banco de dados. Para impedir que um logon tenha a capacidade de detectar um banco de dados, use REVOKE para a permissão VIEW ANY DATABASE da função pública ou DENY para a permissão VIEW ANY DATABASE para logons individuais.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-returning-the-database-id-of-the-current-database"></a>A. Retornando a ID do banco de dados atual  
O exemplo a seguir retorna a ID do banco de dados atual.
  
```sql
SELECT DB_ID() AS [Database ID];  
GO  
```  
  
### <a name="b-returning-the-database-id-of-a-specified-database"></a>B. Retornando a ID de um banco de dados especificado  
O exemplo a seguir retorna a ID do banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql
SELECT DB_ID(N'AdventureWorks2008R2') AS [Database ID];  
GO  
```  
  
### <a name="c-using-dbid-to-specify-the-value-of-a-system-function-parameter"></a>C. Usando DB_ID para especificar o valor de um parâmetro de função do sistema  
O exemplo a seguir usa `DB_ID` para retornar a ID do banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] na função do sistema `sys.dm_db_index_operational_stats`. A função aceita um ID de banco de dados como o primeiro parâmetro.
  
```sql
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-return-the-id-of-the-current-database"></a>D. Retornar a ID do banco de dados atual  
O exemplo a seguir retorna a ID do banco de dados atual.
  
```sql
SELECT DB_ID();  
```  
  
### <a name="e-return-the-id-of-a-named-database"></a>E. Retornar a ID de um banco de dados nomeado.  
O exemplo a seguir retorna a ID do banco de dados AdventureWorksDW2012.
  
```sql
SELECT DB_ID('AdventureWorksPDW2012');  
```  
  
## <a name="see-also"></a>Confira também
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
[Funções de metadados &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)
  
  

