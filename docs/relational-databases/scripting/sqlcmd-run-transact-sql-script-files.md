---
title: Executar arquivos de script Transact-SQL usando sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ee3e53e4d6cfeba2e1cedf2a2c6e3a5500f0e633
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
---
# <a name="sqlcmd---run-transact-sql-script-files"></a>sqlcmd – Executar arquivos de script do Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 Use **sqlcmd** para executar um arquivo de script do Transact-SQL. Um arquivo de script do Transact-SQL é um arquivo de texto que pode conter uma combinação de instruções Transact-SQL, comandos **sqlcmd** e variáveis de script.  

## <a name="create-a-script-file"></a>Criar um arquivo de script  
 Para criar um arquivo de script simples do Transact-SQL usando o Bloco de Notas, siga estas etapas:  
  
1.  Clique em **Iniciar**, selecione **Todos os Programas**, vá até **Acessórios**e, depois, clique em **Bloco de Notas**.  
  
2.  Copie e cole o seguinte código do Transact-SQL no Bloco de Notas:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  Salve o arquivo como **myScript.sql** na unidade C.  
  
## <a name="run-the-script-file"></a>Executar o arquivo de script  
  
1.  Abra uma janela do prompt de comando.  
  
2.  Na janela do Prompt de Comando, digite: **sqlcmd -S myServer\nomeInstância -i C:\myScript.sql**  
  
3.  Pressione ENTER.  
  
 Uma lista de nomes e endereços de funcionários do [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] é escrita na janela do prompt de comando.  

## <a name="save-the-output-to-a-text-file"></a>Salvar a saída em um arquivo de texto
  
1.  Abra uma janela do prompt de comando.  
  
2.  Na janela do Prompt de comando, digite: **sqlcmd -S myServer\nomeInstância -i C:\myScript.sql -o C:\EmpAdds.txt**  
  
3.  Pressione ENTER.  
  
 Nenhuma saída é retornada na janela de prompt de comando. Em vez disso, a saída é enviada ao arquivo EmpAdds.txt. Você pode verificar essa saída abrindo o arquivo EmpAdds.txt.  
  
## <a name="see-also"></a>Consulte Também  
 [Iniciar o utilitário sqlcmd](../../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [Utilitário sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
