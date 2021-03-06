---
title: DECRYPTBYKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DecryptByKey_TSQL
- DECRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], DecryptByKey function
- decryption [SQL Server], keys
- decryption [SQL Server], symmetric keys
- DECRYPTBYKEY function
ms.assetid: 6edf121f-ac62-4dae-90e6-6938f32603c9
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 57a2175b3c4096ab9af7203d7f7d3733947f8e78
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="decryptbykey-transact-sql"></a>DECRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Decifra dados usando uma chave simétrica.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
DecryptByKey ( { 'ciphertext' | @ciphertext }   
    [ , add_authenticator, { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *ciphertext*  
 São os dados que foram criptografados com a chave. O *ciphertext* é **varbinary**.  
  
 **@ciphertext**  
 É uma variável do tipo **varbinary** que contém dados criptografados com a chave.  
  
 *add_authenticator*  
 Indica se um autenticador foi criptografado junto com o texto não criptografado. Deve ser igual ao valor passado para EncryptByKey durante a criptografia dos dados. *add_authenticator* é **int**.  
  
 *authenticator*  
 São os dados a partir dos quais um autenticador é gerado. Deve corresponder ao valor fornecido para EncryptByKey. O *authenticator* é **sysname**.  
  
 **@authenticator**  
 É uma variável que contém dados a partir dos quais um autenticador é gerado. Deve corresponder ao valor fornecido para EncryptByKey.  
  
## <a name="return-types"></a>Tipos de retorno  
 **varbinary** com um tamanho máximo de 8.000 bytes.
 
Retorna NULL se a chave simétrica usada para criptografar os dados não está aberta ou o *ciphertext* é NULL.
  
## <a name="remarks"></a>Remarks  
 DecryptByKey usa uma chave simétrica. Essa chave simétrica já deve estar aberta no banco de dados. Podem haver várias chaves abertas ao mesmo tempo. Não é necessário abrir a chave imediatamente antes de descriptografar o texto de codificado.  
  
 A criptografia e a descriptografia simétricas são relativamente rápidas e adequadas para trabalhar com grandes quantidades de dados.  
  
## <a name="permissions"></a>Permissões  
 Requer que a chave simétrica tenha sido aberta na sessão atual. Para obter mais informações, consulte [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md).  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-decrypting-by-using-a-symmetric-key"></a>A. Descriptografando com o uso de uma chave simétrica  
 O exemplo a seguir descriptografa texto codificado usando uma chave simétrica.  
  
```  
-- First, open the symmetric key with which to decrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
GO  
  
-- Now list the original ID, the encrypted ID, and the   
-- decrypted ciphertext. If the decryption worked, the original  
-- and the decrypted ID will match.  
SELECT NationalIDNumber, EncryptedNationalID   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalID))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-decrypting-by-using-a-symmetric-key-and-an-authenticating-hash"></a>B. Descriptografando com o uso de uma chave simétrica e um hash de autenticação  
 O exemplo a seguir descriptografa dados que foram criptografados junto com um autenticador.  
  
```  
-- First, open the symmetric key with which to decrypt the data  
OPEN SYMMETRIC KEY CreditCards_Key11  
   DECRYPTION BY CERTIFICATE Sales09;  
GO  
  
-- Now list the original card number, the encrypted card number,  
-- and the decrypted ciphertext. If the decryption worked,   
-- the original number will match the decrypted number.  
SELECT CardNumber, CardNumber_Encrypted   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByKey(CardNumber_Encrypted, 1 ,   
    HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))   
    AS 'Decrypted card number' FROM Sales.CreditCard;  
GO  
  
```  
  
## <a name="see-also"></a>Consulte Também  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Hierarquia de criptografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Escolher um algoritmo de criptografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  
