---
title: MSSQLSERVER_3168 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3168 (Database Engine error)
ms.assetid: 991111d9-1eb3-43e9-9333-a75a775c3200
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f3fba8e081265cf95969f1e1dbeff80222e3538a
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver3168"></a>MSSQLSERVER_3168
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID do evento|3168|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|LDDB_SYSTEMWRONGVER|  
|Texto da mensagem|O backup do banco de dados do sistema no dispositivo %ls não pode ser restaurado porque foi criado por uma versão diferente (%ls) da versão deste servidor (%ls).|  
  
## <a name="explanation"></a>Explicação  
Não é possível restaurar um backup de um banco de dados do sistema (**master**, **model** ou **msdb**) em um build do servidor diferente do build em que o backup foi originalmente executado.  
  
> [!NOTE]  
> A instalação de uma compilação de service pack ou de hotfix altera o número de compilação do servidor e as compilações do servidor são sempre incrementais.  
  
### <a name="possible-causes"></a>Causas possíveis  
O esquema de banco de dados para os bancos de dados do sistema pode ter sido alterado nas compilações do servidor. Para certificar-se de que uma alteração de esquema não cause inconsistências, a instrução RESTORE compara o número de compilação do servidor no arquivo de backup com o número de compilação do servidor no qual você está tentando restaurar o backup. Se as compilações forem diferentes, a instrução emitirá uma mensagem de erro 3168 e a operação de restauração será terminada de forma anormal.  
  
Alguns cenários nos quais esse problema pode acontecer incluem os seguintes:  
  
-   Um usuário tenta restaurar um banco de dados do sistema no servidor A partir de um backup executado no servidor B. Os servidores A e B estão em diferentes compilações do servidor. Por exemplo, o servidor A pode estar em uma compilação da versão original e o servidor B pode estar em uma compilação de service pack 1 (SP1).  
  
-   Um usuário tenta restaurar um banco de dados do sistema a partir de um backup executado no mesmo servidor. Porém, o servidor estava executando uma compilação diferente quando o backup aconteceu. Isto é, o servidor foi atualizado desde a realização do backup.  
  
## <a name="user-action"></a>Ação do usuário  
O processo de restauração nessa situação está claramente envolvido e só é usado em último caso. Para obter mais informações, consulte “[Não é possível restaurar backups de banco de dados do sistema em um build diferente do SQL Server](http://support.microsoft.com/kb/264474)”.  
  
## <a name="see-also"></a>Consulte Também  
[Fazer backup e restaurar bancos de dados do sistema &#40;SQL Server&#41;](~/relational-databases/backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
