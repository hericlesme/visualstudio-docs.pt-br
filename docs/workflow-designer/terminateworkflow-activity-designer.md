---
title: Designer de atividade de TerminateWorkflow | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 683c482436e968ff9d2a1bd4ce0bbb8e173a5520
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="terminateworkflow-activity-designer"></a>Designer de atividade de TerminateWorkflow
O **TerminateWorkflow** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.TerminateWorkflow> atividade.

## <a name="the-terminateworkflow-activity"></a>A atividade de TerminateWorkflow
 A atividade de <xref:System.Activities.Statements.TerminateWorkflow> finaliza a execução de um fluxo de trabalho.

### <a name="using-the-terminateworkflow-activity-designer"></a>Usando o designer de atividade de TerminateWorkflow
 O **TerminateWorkflow** designer de atividade pode ser encontrado no **tempo de execução** categoria do **caixa de ferramentas**, que é acessado clicando o **dacaixadeferramentas** guia (como alternativa, selecione **caixa de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **TerminateWorkflow** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.TerminateWorkflow> atividade com um padrão **DisplayName** de TerminateWorkflow. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **TerminateWorkflow** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

### <a name="the-terminateworkflow-properties"></a>As propriedades de TerminateWorkflow
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.TerminateWorkflow> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.TerminateWorkflow> . O padrão é TerminateWorkflow. Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|A exceção para indicar quando o fluxo de trabalho é encerrado. Defina essa propriedade na grade de propriedade.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|A razão que explica como o fluxo de trabalho foi encerrado. Defina essa propriedade na grade de propriedade.|

## <a name="see-also"></a>Consulte também

- [Tempo de execução](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)