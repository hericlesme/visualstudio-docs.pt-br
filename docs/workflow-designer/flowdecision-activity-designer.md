---
title: Designer de fluxo de trabalho - Designer de atividade de FlowDecision
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 033eeff34c095b4598a02a386794379d06086450
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="flowdecision-activity-designer"></a>Designer de atividade de FlowDecision

O nó de <xref:System.Activities.Statements.FlowDecision> é um nó condicional que fornece uma ramificação para o fluxo de controle em uma das duas alternativas com base em se uma condição especificada é satisfeita. Se o fluxo requer mais de duas ramificações, use <xref:System.Activities.Statements.FlowSwitch%601> em vez disso.

## <a name="the-flowdecision-node"></a>O nó de FlowDecision

Use <xref:System.Activities.Statements.FlowDecision> quando o fluxo pode ser transformada em dois caminhos. Um nó de <xref:System.Activities.Statements.FlowDecision> tem <xref:System.Activities.Statements.FlowDecision.Condition%2A> e <xref:System.Activities.Statements.FlowNode> associados a cada um dos dois resultados possíveis: <xref:System.Activities.Statements.FlowDecision.True%2A> ou <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> é avaliado e o valor da avaliação determina <xref:System.Activities.Statements.FlowNode> a seguir seja processado dentro de <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Utilizando o designer de FlowDecision
 O **FlowDecision** designer pode ser encontrado no **fluxograma** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas** guia no Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **FlowDecision** designer pode ser arrastado o **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho em um **fluxograma** designer de atividade. Isso cria uma <xref:System.Activities.Statements.FlowDecision> rotulada **decisão** dentro de <xref:System.Activities.Statements.Flowchart> atividade. Passe o mouse sobre o designer e o **True** e **False** aparecem alças quadradas para duas ramificações.

 Depois de arrastar o **FlowDecision** designer e outros designers para o **fluxograma**, os nós podem ser vinculados juntos para especificar a ordem de execução. Para criar um link entre um nó de origem (incluindo o **True** e **False** ramificações dos **FlowDecision**) e um nó de destino, passe o mouse sobre o designer do nó de origem e alças quadradas aparecerão em cada lado dela. Clique em uma das alças de quadradas e arraste-a segurando o botão do mouse na uma das alças que aparece de maneira similar ao redor do nó de destino quando você o mouse sobre ele. Liberar o botão do mouse e um link é criado no meio esses dois nós que é representado como uma seta do designer de origem para o designer de destino.

 A expressão que define o <xref:System.Activities.Statements.FlowDecision.Condition%2A> podem ser digitados no **condição** caixa do **propriedades** janela clicando em que o texto de dica dizendo "Insira uma expressão VB".

### <a name="the-flowdecision-properties"></a>As propriedades de FlowDecision
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.FlowDecision> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|verdadeiro|A condição que determina que caminho o controle de fluxo leva.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|O caminho tomada pelo controle de fluxo se <xref:System.Activities.Statements.FlowDecision.Condition%2A> estiver satisfeito.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|O caminho tomada pelo controle de fluxo se <xref:System.Activities.Statements.FlowDecision.Condition%2A> não estiver satisfeito.|

## <a name="see-also"></a>Consulte também

- [Fluxograma](../workflow-designer/flowchart-activity-designers.md)
- [Fluxograma](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)