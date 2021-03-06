---
title: PDOStatement::errorInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e45bebe8-ea4c-49b6-93db-cf1ae65f530c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46c2cda3b7b36d534e02a8a4d3a782e3abd94240
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="pdostatementerrorinfo"></a>PDOStatement::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera informações de erro estendidas da operação mais recente no identificador da instrução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array PDOStatement::errorInfo();  
```  
  
## <a name="return-value"></a>Valor de retorno  
Uma matriz de informações de erro sobre a operação mais recente no identificador da instrução. A matriz consiste nos seguintes campos:  
  
-   O código de erro SQLSTATE  
  
-   O código de erro específico do driver  
  
-   A mensagem de erro específica do driver  
  
Se não houver nenhum erro ou se o SQLSTATE não for definido, os campos específicos do driver serão NULL.  
  
## <a name="remarks"></a>Remarks  
O suporte para PDO foi adicionado na versão 2.0 dos [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemplo  
Neste exemplo, a instrução SQL tem um erro, que é relatado em seguida.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print_r ($stmt->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>Consulte também  
[PDOStatement Class](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
