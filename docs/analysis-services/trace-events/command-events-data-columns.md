---
title: Colunas de dados de eventos de comando | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ef4275eb57228ab31cac346a4dcbf6cfbdd39976
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="command-events-data-columns"></a>Colunas de dados de eventos de comando
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  A tabela a seguir lista as colunas de dados de cada classe de evento na categoria **Eventos de Comando** .  
  
 A categoria **Eventos de Comando** tem as seguintes classes de evento:  
  
-   [Classe Command Begin](#bkmk_1)  
  
-   [Classe Command End](#bkmk_2)  
  
 As tabelas a seguir listam as colunas de dados de cada uma dessas classes de evento.  
  
##  <a name="bkmk_1"></a> Classe Command Begin - Colunas de dados  
  
|Coluna de dados|Description|  
|-----------------|-----------------|  
|ConnectionID|Contém a ID de conexão exclusiva associada ao evento de comando.|  
|TextData|Contém os dados de texto associados ao evento de comando.|  
|ServerName|Contém o nome da instância do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] na qual o evento de comando ocorreu.|  
|CurrentTime|Contém a hora atual do evento de comando.|  
|DatabaseName|Contém o nome do banco de dados no qual o comando está em execução.|  
|EventSubclass|Contém a classe do evento de comando. Os valores com suporte são:<br /><br /> 0: Criar<br /><br /> 1: Alterar<br /><br /> 2: Excluir<br /><br /> 3: Processar<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restaurar<br /><br /> 10: MergePartitions<br /><br /> 11: Assinar<br /><br /> 12: Lote<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancelar<br /><br /> 18: Sincronizar<br /><br /> 19: Import80MiningModels<br /><br /> 20: Anexar<br /><br /> 21: Desanexar<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Outro|  
|NTUserName|Contém o nome de usuário do Windows associado ao evento de comando. O nome de usuário está na forma canônica. Por exemplo, engineering.microsoft.com/software/user.|  
|RequestProperties|Contém as propriedades de solicitação de XML for Analysis (XMLA) associadas ao evento de comando.|  
|SPID|Contém a SPID (ID do processo do servidor) que identifica de modo exclusivo a sessão de usuário associada ao evento de comando. A SPID corresponde diretamente à GUID de sessão usada pelo XMLA.|  
|StartTime|Contém a hora em que o evento de comando foi iniciado, se disponível.|  
|SessionType|Contém a entidade que causou a operação.|  
|NTDomainName|Contém a conta de domínio do Windows associada ao evento de permissão de objetos.|  
|ClientProcessID|Contém a ID de processo de cliente exclusiva associada ao evento de comando.|  
  
##  <a name="bkmk_2"></a> Classe Command End - Colunas de dados  
  
|Coluna de dados|Description|  
|-----------------|-----------------|  
|ConnectionID|Contém a ID de conexão exclusiva associada ao evento de comando.|  
|TextData|Contém os dados de texto associados ao evento de comando.|  
|ServerName|Contém o nome da instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] na qual o evento de comando ocorreu.|  
|CurrentTime|Contém a hora atual do evento de comando. Para filtragem, os formatos são *AAAA*-*MM*-*DD* e *AAAA*-*MM*-*DD HH*:*MM*:*SS*.|  
|DatabaseName|Contém o nome do banco de dados no qual o comando está em execução.|  
|Duration|Contém o período de tempo aproximado entre o evento de comando inicial e final.|  
|EndTime|Contém a hora em que o evento de comando terminou. Para filtragem, os formatos são *AAAA*-*MM*-*DD* e *AAAA*-*MM*-*DD HH*:*MM*:*SS*.|  
|EventSubclass|Contém a classe do evento de comando. Os valores com suporte são:<br /><br /> 0: Criar<br /><br /> 1: Alterar<br /><br /> 2: Excluir<br /><br /> 3: Processar<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restaurar<br /><br /> 10: MergePartitions<br /><br /> 11: Assinar<br /><br /> 12: Lote<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancelar<br /><br /> 18: Sincronizar<br /><br /> 19: Import80MiningModels<br /><br /> 20: Anexar<br /><br /> 21: Desanexar<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Outro|  
|NTCanonicalUserName|Contém o nome de usuário do Windows associado ao evento de comando. O nome de usuário está na forma canônica. Por exemplo, engineering.microsoft.com/software/user.|  
|NTUserName|Contém a conta de usuário do Windows associada ao evento de comando.|  
|SPID|Contém a identificação do processo do servidor (SPID) que identifica de modo exclusivo a sessão de usuário associada ao evento de comando. A SPID corresponde diretamente à GUID de sessão usada pelo XMLA.|  
|StartTime|Contém a hora em que o evento de comando final foi iniciado, se disponível.|  
|CPUTime|Contém o período de tempo da CPU (em milissegundos) usado pelo processo entre o início e o término do evento de comando.|  
|Erro|Contém o número de erro de qualquer erro associado ao evento de comando.|  
|Severity|Contém o nível de severidade de uma exceção associada ao evento de comando. Os valores são:<br /><br /> 0 = Êxito<br /><br /> 1 = Informativo<br /><br /> 2 = Aviso<br /><br /> 3 = Erro|  
|Success|Contém o êxito ou a falha do evento de comando. Os valores são:<br /><br /> 0 = Falha<br /><br /> 1 = Êxito|  
|SessionType|Contém a entidade que causou a operação associada ao evento de comando final.|  
|NTDomainName|Contém a conta de domínio do Windows associada ao evento de comando.|  
|ClientProcessID|Contém a ID de processo de cliente exclusiva associada ao evento de comando.|  
  
## <a name="see-also"></a>Consulte também  
 [Categoria de evento de eventos de comando](../../analysis-services/trace-events/command-events-event-category.md)  
  
  
