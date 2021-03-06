---
title: Método STAT | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26dd4f3fa7de49f51c32fd97e184ee356cb16f35
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="stat-method"></a>Método STAT
Recupera informações sobre um [fluxo](../../../ado/reference/ado-api/stream-object-ado.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Um **longo** valor que indica o status da operação.  
  
#### <a name="parameters"></a>Parâmetros  
 *StatStg*  
 Uma estrutura STATSTG que será preenchida com informações sobre o fluxo. A implementação de **Stat** método usado pelo objeto de fluxo ADO não Preencha todos os campos da estrutura.  
  
 *StatFlag*  
 Especifica que este método não retorna alguns dos membros na estrutura STATSTG, economizando uma operação de alocação de memória. Os valores são obtidos da enumeração STATFLAG. A enumeração STATFLAG tem dois valores  
  
|Constante|Value|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Remarks  
 A versão do método Stat implementado para o objeto de fluxo ADO preenche os campos a seguir da estrutura de STATSTG:  
  
 *pwcsName*  
 Uma cadeia de caracteres que contém o nome do fluxo, se disponível e o valor de StatFlag STATFLAG_NONAME não foi especificada.  
  
 *cbSize*  
 Especifica o tamanho em bytes da matriz de bytes ou fluxo.  
  
 *mtime*  
 Indica a hora da última modificação para este armazenamento, fluxo ou matriz de bytes.  
  
 *ctime*  
 Indica a hora de criação para este armazenamento, fluxo ou matriz de bytes.  
  
 *atime*  
 Indica a hora do último acesso para este armazenamento, fluxo ou matriz de bytes.  
  
 Se STATFLAG_NONAME for especificado no parâmetro StatFlag, o nome do fluxo não é retornado.  
  
 Se STATFLAG_NONAME não foi especificado no parâmetro StatFlag e não há nenhum nome disponível para o fluxo atual, esse valor será E_NOTIMPL.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
