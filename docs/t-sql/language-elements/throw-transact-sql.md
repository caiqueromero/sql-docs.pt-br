---
title: THROW (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- THROW_TSQL
- THROW
dev_langs:
- TSQL
helpviewer_keywords:
- THROW statement
ms.assetid: 43661b89-8f13-4480-ad53-70306cbb14c5
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7e61cb9edc75dda4368e31e9eac6e4e452d4387f
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="throw-transact-sql"></a>THROW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Gera uma exceção e transfere a execução para um bloco CATCH de uma construção TRY…CATCH no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
THROW [ { error_number | @local_variable },  
        { message | @local_variable },  
        { state | @local_variable } ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *ERROR_NUMBER*  
 É uma constante ou uma variável que representa a exceção. *ERROR_NUMBER* é **int** e deve ser maior ou igual a 50000 e menor ou igual a 2147483647.  
  
 *Mensagem*  
 É uma cadeia de caracteres ou variável que descreve a exceção. *mensagem* é **nvarchar (2048)**.  
  
 *estado*  
 É uma constante ou variável entre 0 e 255 que indica o estado a ser associado à mensagem. *estado* é **tinyint**.  
  
## <a name="remarks"></a>Comentários  
 A instrução antes de THROW deve ser seguida pelo terminador de instrução ponto-e-vírgula (;).  
  
 Se uma construção TRY…CATCH não estiver disponível, a sessão será encerrada. O número da linha e o procedimento em que a exceção foi gerada estão definidos. A severidade é definida como 16.  
  
 Se a instrução THROW for especificada sem parâmetros, ela deverá aparecer dentro de um bloco CATCH. Isso faz com que a exceção capturada seja gerada. Qualquer erro que ocorra em uma instrução THROW faz com que o lote de instruções seja encerrado.  
  
 % é um caractere reservado no texto da mensagem de uma instrução THROW e deve ser substituído. Dobrar o caractere % para retornar % como parte do texto da mensagem, por exemplo 'o aumento excedeu 15% do valor original.'  
  
## <a name="differences-between-raiserror-and-throw"></a>Diferenças entre RAISERROR e THROW  
 A tabela a seguir lista as diferenças entre as instruções RAISERROR e THROW.  
  
|instrução RAISERROR|instrução THROW|  
|-------------------------|---------------------|  
|Se um *msg_id* é passada para RAISERROR, a ID deve ser definida em sys. messages.|O *error_number* parâmetro não precisa ser definida em sys. messages.|  
|O *msg_str* parâmetro pode conter **printf** estilos de formatação.|O *mensagem* parâmetro não aceitará **printf** formatação de estilo.|  
|O *severidade* parâmetro especifica a severidade da exceção.|Não há nenhum *severidade* parâmetro. A severidade de exceção sempre é definida como 16.|  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-using-throw-to-raise-an-exception"></a>A. Usando THROW para gerar uma exceção  
 O exemplo a seguir mostra como usar o `THROW` instrução para gerar uma exceção.  
  
```tsql  
THROW 51000, 'The record does not exist.', 1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 51000, Level 16, State 1, Line 1`  
  
 `The record does not exist.`  
  
### <a name="b-using-throw-to-raise-an-exception-again"></a>B. Usando THROW para gerar uma exceção novamente  
 O exemplo a seguir mostra como usar a instrução `THROW` para gerar a última exceção lançada novamente.  
  
```tsql  
USE tempdb;  
GO  
CREATE TABLE dbo.TestRethrow  
(    ID INT PRIMARY KEY  
);  
BEGIN TRY  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
--  Force error 2627, Violation of PRIMARY KEY constraint to be raised.  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
END TRY  
BEGIN CATCH  
  
    PRINT 'In catch block.';  
    THROW;  
END CATCH;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `PRINT 'In catch block.';`  
  
 `Msg 2627, Level 14, State 1, Line 1`  
  
 `Violation of PRIMARY KEY constraint 'PK__TestReth__3214EC272E3BD7D3'. Cannot insert duplicate key in object 'dbo.TestRethrow'.`  
  
 `The statement has been terminated.`  
  
### <a name="c-using-formatmessage-with-throw"></a>C. Usando FORMATMESSAGE com THROW  
 O exemplo a seguir mostra como usar a função `FORMATMESSAGE` com `THROW` para lançar uma mensagem de erro personalizada. O exemplo cria primeiro uma mensagem de erro definida pelo usuário usando `sp_addmessage`. Porque a instrução THROW não permite parâmetros de substituição no *mensagem* parâmetro da forma RAISERROR faz, a função FORMATMESSAGE é usado para transmitir os três valores de parâmetro esperados pela mensagem de erro 60000.  
  
```tsql  
EXEC sys.sp_addmessage  
     @msgnum   = 60000  
,@severity = 16  
,@msgtext  = N'This is a test message with one numeric parameter (%d), one string parameter (%s), and another string parameter (%s).'  
    ,@lang = 'us_english';   
GO  
  
DECLARE @msg NVARCHAR(2048) = FORMATMESSAGE(60000, 500, N'First string', N'second string');   
  
THROW 60000, @msg, 1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 60000, Level 16, State 1, Line 2`  
  
 `This is a test message with one numeric parameter (500), one string parameter (First string), and another string parameter (second string).`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-throw-to-raise-an-exception"></a>D. Usando THROW para gerar uma exceção  
 O exemplo a seguir mostra como usar o `THROW` instrução para gerar uma exceção.  
  
```tsql  
THROW 51000, 'The record does not exist.', 1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 51000, Level 16, State 1, Line 1`  
  
 `The record does not exist.`  
  
## <a name="see-also"></a>Consulte também  
 [FORMATMESSAGE &#40; Transact-SQL &#41;](../../t-sql/functions/formatmessage-transact-sql.md)   
 [Severidade de erro do mecanismo de banco de dados](../../relational-databases/errors-events/database-engine-error-severities.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [Ir para &#40; Transact-SQL &#41;](../../t-sql/language-elements/goto-transact-sql.md)   
 [BEGIN... FINAL &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [XACT_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/xact-state-transact-sql.md)   
 [SET XACT_ABORT &#40; Transact-SQL &#41;](../../t-sql/statements/set-xact-abort-transact-sql.md)  
  
  

