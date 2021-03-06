---
title: Propriedade SQL | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5ddbfa6b69f4859f61130e8ec1c9b758c40cf64
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sql-property"></a>Propriedade SQL
Indica a cadeia de caracteres de consulta usada para recuperar o [registros](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Você pode definir o **SQL** propriedade em tempo de design a [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) marcas de objeto do objeto, ou em tempo de execução no código de script.  
  
> [!IMPORTANT]
>  Começando com o Windows 8 e Windows Server 2012, os componentes de servidor RDS não estão mais incluídos no sistema operacional Windows (veja o Windows 8 e [manual de compatibilidade do Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obter mais detalhes). Componentes de cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Aplicativos que usam o RDS devem migrar para [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *QueryString*  
 Um **cadeia de caracteres** valor que contém uma solicitação de dados do SQL válida.  
  
 *DataControl*  
 Uma variável de objeto que representa um **RDS. DataControl** objeto.  
  
## <a name="remarks"></a>Remarks  
 Em geral, isso é uma instrução SQL (usando o dialeto do servidor de banco de dados), como `"Select * from NewTitles"`. Para garantir que os registros são correspondentes e atualizados com precisão, uma consulta atualizável deve conter um campo que não seja um campo binário longo ou um campo computado.  
  
 O **SQL** propriedade é opcional se um objeto de negócios personalizada do lado do servidor recupera os dados para o cliente.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo da propriedade SQL (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [Conecte-se a propriedade (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Método Query (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Atualizar o método (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Método SubmitChanges (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


