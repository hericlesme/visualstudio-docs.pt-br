---
title: Designer de fluxo de trabalho - se o Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58adde57c6de49a4abb0456ba5c80df27a45b069
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="if-activity-designer"></a>Se designer de atividades

A atividade de <xref:System.Activities.Statements.If> avalia uma condição e executa uma atividade dependendo dos resultados da avaliação. Esta atividade é mais útil ao usar um estilo modelando procedural de programação. Uma atividade de <xref:System.Activities.Statements.If> pode ser aninhadas dentro de uma atividade de <xref:System.Activities.Statements.Sequence> ou uma atividade de <xref:System.Activities.Statements.Parallel> , por exemplo. Se você estiver usando uma atividade de <xref:System.Activities.Statements.Flowchart> , considere usar uma atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.

## <a name="if-properties-in-the-workflow-designer"></a>Se as propriedades em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.If> e descreve como usá-los no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|verdadeiro|A condição que determina que atividade filho para executar. Para definir o <xref:System.Activities.Statements.If.Condition%2A>, digite uma expressão do Visual Basic no **condição** caixa o **se** atividade designer ou na grade de propriedades.|
|<xref:System.Activities.Statements.If.Else%2A>|False|A atividade seja executada se o <xref:System.Activities.Statements.If.Condition%2A> é **false**. Para adicionar uma atividade que é executada pelo <xref:System.Activities.Statements.If.Else%2A> branch, remover uma atividade do **caixa de ferramentas** no **Else** caixa o **se** designer de atividade com o texto de dica " Descartar atividade aqui".|
|<xref:System.Activities.Statements.If.Then%2A>|False|A atividade seja executada se o <xref:System.Activities.Statements.If.Condition%2A> é **true**. Para adicionar uma atividade que é executada pelo <xref:System.Activities.Statements.If.Then%2A> branch, remover uma atividade do **caixa de ferramentas** no **, em seguida,** caixa o **se** designer de atividade com o texto de dica " Descartar atividade aqui".|

## <a name="see-also"></a>Consulte também

- [sequência](../workflow-designer/sequence-activity-designer.md)
- [Paralelo](../workflow-designer/parallel-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)