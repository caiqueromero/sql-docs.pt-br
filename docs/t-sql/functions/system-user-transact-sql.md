---
title: SYSTEM_USER (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSTEM_USER_TSQL
- SYSTEM_USER
dev_langs:
- TSQL
helpviewer_keywords:
- current user names
- system-supplied user names [SQL Server]
- users [SQL Server], logins
- logins [SQL Server], identification name
- current system user names
- SYSTEM_USER function
- inserting system user name into table
- system usernames [SQL Server]
- users [SQL Server], names
ms.assetid: 565984cd-60c6-4df7-83ea-2349b838ccb2
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d3f13d5db5d7787a60c455edc64644f4c23779fc
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="systemuser-transact-sql"></a>SYSTEM_USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Permite que um valor fornecido pelo sistema para o logon atual seja inserido em uma tabela quando nenhum valor padrão é especificado.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SYSTEM_USER  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 **nchar**  
  
## <a name="remarks"></a>Comentários  
 É possível usar a função SYSTEM_USER com restrições DEFAULT nas instruções CREATE TABLE e ALTER TABLE. Ela também pode ser usada como qualquer função padrão.  
  
 Se o nome de usuário e o nome de logon forem diferentes, SYSTEM_USER retornará o nome de logon.  
  
 Se o usuário atual está conectado ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando a autenticação do Windows, SYSTEM_USER retornará o nome de identificação de logon do Windows no formato: *domínio*\\*nome_de_logon_do_usuário*. Entretanto, se o usuário atual tiver feito logon no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando a Autenticação do SQL Server, SYSTEM_USER retornará o nome de identificação de logon do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], como `WillisJo` para um usuário conectado como `WillisJo`.  
  
 SYSTEM_USER retorna o nome do contexto em execução no momento. Se a instrução EXECUTE AS tiver sido usada para alternar o contexto, SYSTEM_USER retornará o nome do contexto representado.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-using-systemuser-to-return-the-current-system-user-name"></a>A. Usando SYSTEM_USER para retornar o nome de usuário do sistema atual  
 O exemplo a seguir declara uma variável `char`, armazena o valor atual `SYSTEM_USER` na variável e imprime o valor armazenado na variável.  
  
```  
DECLARE @sys_usr char(30);  
SET @sys_usr = SYSTEM_USER;  
SELECT 'The current system user is: '+ @sys_usr;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `----------------------------------------------------------`  
  
 `The current system user is: WillisJo`  
  
 `(1 row(s) affected)`  
  
### <a name="b-using-systemuser-with-default-constraints"></a>B. Usando SYSTEM_USER com restrições DEFAULT  
 O exemplo a seguir cria uma tabela com a restrição `SYSTEM_USER` como uma restrição `DEFAULT` para a coluna `SRep_tracking_user`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE Sales.Sales_Tracking  
(  
    Territory_id int IDENTITY(2000, 1) NOT NULL,  
    Rep_id  int NOT NULL,  
    Last_sale datetime NOT NULL DEFAULT GETDATE(),  
    SRep_tracking_user varchar(30) NOT NULL DEFAULT SYSTEM_USER  
);  
GO  
INSERT Sales.Sales_Tracking (Rep_id)  
VALUES (151);  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (293, '19980515');  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (27882, '19980620');  
INSERT Sales.Sales_Tracking (Rep_id)  
VALUES (21392);  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (24283, '19981130');  
GO  
```  
  
 A consulta a seguir seleciona todas a informações da tabela `Sales_Tracking`:  
  
```  
SELECT * FROM Sales_Tracking ORDER BY Rep_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Territory_id Rep_id Last_sale            SRep_tracking_user`  
  
 `-----------  ------ -------------------- ------------------`  
  
 `2000         151    Mar 4 1998 10:36AM   ArvinDak`  
  
 `2001         293    May 15 1998 12:00AM  ArvinDak`  
  
 `2003         21392  Mar 4 1998 10:36AM   ArvinDak`  
  
 `2004         24283  Nov 3 1998 12:00AM   ArvinDak`  
  
 `2002         27882  Jun 20 1998 12:00AM  ArvinDak`  
  
 `(5 row(s) affected)`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-systemuser-to-return-the-current-system-user-name"></a>C: usando SYSTEM_USER para retornar o nome de usuário do sistema atual  
 O exemplo a seguir retorna o valor atual de `SYSTEM_USER`.  
  
```  
SELECT SYSTEM_USER;  
```  
  
## <a name="see-also"></a>Consulte também  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40; Transact-SQL &#41;](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER &#40; Transact-SQL &#41;](../../t-sql/functions/current-user-transact-sql.md)   
 [SESSION_USER &#40; Transact-SQL &#41;](../../t-sql/functions/session-user-transact-sql.md)   
 [Funções de sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [USUÁRIO &#40; Transact-SQL &#41;](../../t-sql/functions/user-transact-sql.md)  
  
  

