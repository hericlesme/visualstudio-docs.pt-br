---
title: Designer de atividade de estado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 
ms.author: sdanie
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 4321ccba1d3081023c8603df04174506df78f288
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="state-activity-designer"></a>Designer de atividade de estado
<xref:System.Activities.Statements.State> representa um estado em que um computador de estado pode estar.  
  
## <a name="using-the-state-activity-designer"></a>Usando o designer de atividade de estado  
 Para adicionar um <xref:System.Activities.Statements.State> um fluxo de trabalho, arraste o **estado** designer de atividade do **máquina de estado** seção do **caixa de ferramentas** e soltá-lo para um <xref:System.Activities.Statements.StateMachine> atividade no [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] superfície. Uma atividade de <xref:System.Activities.Statements.State> pode ser arrastada em <xref:System.Activities.Statements.StateMachine> e as transições adicionados posteriormente; ou uma transição pode ser criada como a atividade de <xref:System.Activities.Statements.State> é descartada. Para adicionar um <xref:System.Activities.Statements.State> atividade e criar uma transição em uma única etapa, arraste um **estado** atividade do **máquina de estado** seção o **caixa de ferramentas** e passe o mouse sobre outra estado no designer de fluxo de trabalho. Quando <xref:System.Activities.Statements.State> arrastado está sobre um outro <xref:System.Activities.Statements.State>, quatro triângulos aparecerão em torno do outro <xref:System.Activities.Statements.State>. Se <xref:System.Activities.Statements.State> é solto em um dos quatro triângulos, é adicionado ao computador de estado e uma transição é criada de origem <xref:System.Activities.Statements.State> ao destino solto <xref:System.Activities.Statements.State>. Para obter mais informações, consulte [transição](../workflow-designer/transition-activity-designer.md).  
  
### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade do estado em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.State> que podem ser definidas usando o designer de fluxo de trabalho e descreve como elas são usadas no designer. Algumas dessas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície de designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.State> no cabeçalho. O valor padrão é **estado**. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade. <xref:System.Activities.Statements.State.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Statements.State.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica a ação que ocorre quando esse estado é feito a transição para. Quando o <xref:System.Activities.Statements.State> atividade é expandida, esse valor pode ser definido, arrastando uma atividade do **caixa de ferramentas** e descarte-a para o **entrada** seção do estado.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Especifica a ação que ocorre quando esse estado é feito a transição fora. Quando o <xref:System.Activities.Statements.State> atividade é expandida, esse valor pode ser definido, arrastando uma atividade do **caixa de ferramentas** e descarte-a para o **Exit** seção do estado.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Lista as transições possíveis que originam de <xref:System.Activities.Statements.State>. Cada item na lista possui um link a <xref:System.Activities.Statements.Transition> associado e de destino <xref:System.Activities.Statements.State>. Clicar no link alternará o designer para uma exibição expandida de <xref:System.Activities.Statements.Transition> ou de <xref:System.Activities.Statements.State>.|  
  
## <a name="see-also"></a>Consulte também  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [Estado final](../workflow-designer/finalstate-activity-designer.md)   
 [Transição](../workflow-designer/transition-activity-designer.md)