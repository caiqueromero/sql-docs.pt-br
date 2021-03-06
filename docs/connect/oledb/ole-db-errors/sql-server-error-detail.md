---
title: Detalhes de erro do SQL Server | Microsoft Docs
description: Detalhes de erros do SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f271da81733649c94f01b06281f7463c8ac719b5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-error-detail"></a>Detalhes de erros do SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  O Driver OLE DB para SQL Server define a interface de erro específico do provedor [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1). A interface retorna mais detalhes sobre um erro do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e é valiosa em caso de falha na execução de comandos ou em operações do conjunto de linhas.  
  
 Há duas maneiras de obter acesso a **ISQLServerErrorInfo** interface.  
  
 O consumidor pode chamar **ierrorrecords:: Getcustomererrorobject** para obter um **ISQLServerErrorInfo** ponteiro, conforme mostrado no exemplo de código a seguir. (Não é necessário obter **ISQLErrorInfo.**) Ambos **ISQLErrorInfo** e **ISQLServerErrorInfo** são objetos de erro OLE DB personalizados, com **ISQLServerErrorInfo** sendo a interface a ser usada para obter informações de erros de servidor, incluindo detalhes como números de linha e de nome de procedimento.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Outra maneira de obter um **ISQLServerErrorInfo** ponteiro é chamar o **QueryInterface** método em uma já obtido **ISQLErrorInfo** ponteiro. Observe que, como **ISQLServerErrorInfo** contém um subconjunto das informações disponíveis de **ISQLErrorInfo**, faz sentido para ir diretamente para **ISQLServerErrorInfo** por meio de **GetCustomerErrorObject**.  
  
 O **ISQLServerErrorInfo** interface expõe uma função de membro, [isqlservererrorinfo:: Geterrorinfo](../../oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). A função retorna um ponteiro para uma estrutura SSERRORINFO e um ponteiro para um buffer de cadeia de caracteres. Ambos os ponteiros de referenciam memória que o consumidor deverá desalocar usando o **IMalloc:: Free** método.  
  
 Os membros da estrutura SSERRORINFO são interpretados pelo consumidor como a seguir.  
  
|Membro|Descrição|  
|------------|-----------------|  
|*pwszMessage*|Mensagem de erro do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Idêntica à cadeia de caracteres retornada em **IErrorInfo:: GetDescription**.|  
|*pwszServer*|O nome da instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para a sessão.|  
|*pwszProcedure*|Se apropriado, o nome do procedimento no qual o erro foi originado. Uma cadeia de caracteres vazia caso contrário.|  
|*lNative*|O número do erro nativo do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Idêntico ao valor retornado no *plNativeError* parâmetro **isqlerrorinfo:: Getsqlinfo**.|  
|*bState*|O estado de uma mensagem de erro do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*bClass*|A severidade de uma mensagem de erro do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Quando aplicável, o número da linha de um procedimento armazenado no qual o erro ocorreu.|  
  
## <a name="see-also"></a>Consulte também  
 [Erros](../../oledb/ole-db-errors/errors.md)   
 [RAISERROR & #40; Transact-SQL & #41;](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
