---
title: Atividades de fluxo de trabalho herdado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 756fa86cf892120b0062e2816f146425ac1b4fa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-workflow-activities"></a>Atividades herdados de fluxo de trabalho
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] inclui um conjunto padrão de atividades que fornecem a funcionalidade para o fluxo de controle, as condições, manipulação de eventos, o gerenciamento de estado, e a comunicação com aplicativos e serviços. Ao criar fluxos de trabalho, você pode usar sistema forneceu as atividades que são fornecidas por [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], ou você pode criar suas próprias atividades personalizados.  
  
 A tabela a seguir lista o conjunto de atividade de para fora da estrutura de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] . Muitas, mas não todas, essas atividades são representados pelos designers de atividade que podem ser acessados a partir de **caixa de ferramentas** do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Para criar uma atividade, arraste seu designer do **caixa de ferramentas** e solte-o na superfície de design.  
  
|Atividade|Descrição|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Usado com o **HandleExternalEventActivity** atividade para comunicações de entrada e saídas com um serviço local. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Usado para conter a lógica de limpeza para uma atividade composta cancelada antes de filhos de quaisquer atividades composto é executar concluído. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Permite que você adicione Visual Basic ou código em c ao fluxo de trabalho. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Uma versão compensável de [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Uma versão compensável de **TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Permite que você chamar código para desfazer ou compensar operações já executadas pelo fluxo de trabalho quando ocorre um erro. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Um wrapper para uma ou mais atividades que executam a compensação de uma atividade TransactionScopeActivity concluída [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [usando a atividade CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Executa atividades filho com base em uma condição que se aplica a [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) atividade em si e com base nas condições que se aplicam separadamente para cada filho. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Permite que você crie os atrasos no fluxo de trabalho que são baseados em um intervalo de tempo limite. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Envolve uma ou mais atividades que são executadas quando ocorre um evento especificado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Fornece uma estrutura para associar eventos com uma atividade. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Executa sua atividade filho principal simultaneamente com um [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Usado para manipular uma exceção de um tipo que você especificar. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Representa uma atividade composta que tem uma lista ordenada de atividades filho do tipo [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Usado em conjunto com o [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) atividade para comunicações de entrada e saídas com um serviço local. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testa uma condição em cada ramificação e executa as atividades na primeira ramificação para a qual a condição é igual a **true**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Representa uma ramificação de uma [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Permite que seu fluxo de trabalho para chamar um serviço Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Permite que seu fluxo de trabalho para chamar outro fluxo de trabalho. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Uma atividade composta que contém apenas [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) atividades filho. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Fornece uma maneira de agendar dois ou mais filhos **SequenceActivity** ramificações da atividade de processamento ao mesmo tempo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Uso representar um conjunto de regras. Uma regra consiste em circunstâncias e em ações resultantes. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Cria várias instâncias de uma única atividade filho. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Fornece uma maneira simples de vincular várias juntos para atividades a execução sequencial. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Especifica uma transição para um novo estado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Representa um estado em um fluxo de trabalho do computador de estado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Usado em uma [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) atividade como um contêiner para as atividades filho que são executadas ao sair do **StateActivity** atividade. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Usado em uma [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) atividade como um contêiner para as atividades filho que são executadas quando inserir o **StateActivity** atividade. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Suspende a operação de seu fluxo de trabalho para ativar a intervenção no caso de alguma condição de erro que requer a atenção especial. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Executa sequencialmente atividades contidas em um domínio sincronizado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Permite que você terminar imediatamente a operação de seu fluxo de trabalho no caso de uma condição de erro. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Permite que você capturar exceções lançadas corporativos como parte de metadados do processo para um fluxo de trabalho. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Fornece uma estrutura para transações e manipulação de exceção. Para obter mais informações, consulte [usando a atividade TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Permite que você a modelagem a ocorrência de uma falha de serviço Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Receber dados de um serviço Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Responde a uma solicitação de serviço Web feita a um fluxo de trabalho. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade de WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Permite que seu fluxo de trabalho para executar um loop até que uma condição seja satisfeita. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Usando a atividade WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]como criar atividades personalizadas, consulte [o desenvolvimento de atividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65023) e [usando o Designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exibições de atividade (herdado)](../workflow-designer/activity-views-legacy.md)  
 Descreve as diferentes exibições de design das atividades.  
  
 [Como adicionar atividades à caixa de ferramentas (herdado)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Mostra como adicionar atividades a caixa de ferramentas.  
  
 [Como criar uma condição de regra declarativa (herdado)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Mostra as etapas para criar uma condição declarativa de regra.  
  
 [Como criar um conjunto de regras de PolicyActivity (herdado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Mostra as etapas para criar um conjunto de regras de PolicyActivity.  
  
 [Como: implementar uma operação do WCF (legados)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Mostra as etapas para implementar uma operação do contrato de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] .  
  
 [Como: chamar uma operação do WCF (legados)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Mostra as etapas para chamar uma operação do contrato de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] .  
  
## <a name="see-also"></a>Consulte também  
 [Atividades do Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Fluxos de trabalho de desenvolvimento](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Desenvolvimento de atividades de fluxo de trabalho](http://go.microsoft.com/fwlink?LinkID=65023)