---
title: Designer de fluxo de trabalho - Designer de atividade de picareta
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f664ac3a22b91780d392e0fef3224cd80b1e7919
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975426"
---
# <a name="pick-activity-designer"></a>Escolha o designer de atividades

A atividade de <xref:System.Activities.Statements.Pick> fornece o fluxo de controle baseado. A atividade executa um dos vários ramificações em resposta a um evento disparando.

## <a name="the-pick-activity"></a>A atividade de picareta

Uma atividade de <xref:System.Activities.Statements.Pick> contém uma coleção de objetos <xref:System.Activities.Statements.PickBranch> , uma que a atividade de <xref:System.Activities.Statements.Pick> pode executar devido a qualquer evento de entrada que serve como um disparador. Dessa forma o Designer de fluxo de trabalho do Windows fornece modelagem de fluxo de controle com base em eventos. Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>. No início de um <xref:System.Activities.Statements.Pick> a execução da atividade, todas as atividades de gatilho de <xref:System.Activities.Statements.PickBranch> elementos estão agendados. Quando a primeira atividade concluir, a atividade correspondente de ação está agendada, e quaisquer atividades restantes do disparador serão canceladas.

### <a name="how-to-use-the-pick-activity-designer"></a>Como usar o designer de atividade de picareta

O **escolher** designer de atividade pode ser encontrado no **fluxo de controle** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia no Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

O **escolher** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que os designers de atividade normalmente são colocadas, por exemplo, dentro de um  **Sequência** designer de atividade. Depois de descartá-lo no Designer de fluxo de trabalho, ele cria um <xref:System.Activities.Statements.Pick> atividade, que, por padrão, contém duas vazio <xref:System.Activities.Statements.PickBranch> atividades como elementos com nomes de Branch1 e Branch2 para exibição. Esses respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propriedade podem ser editados no **PickBranch** cabeçalho de designer de atividade ou dentro de **propriedades** janela para cada ramificação.

Há duas maneiras de adicionar <xref:System.Activities.Statements.PickBranch> atividades para a coleção de um <xref:System.Activities.Statements.Pick> objeto: arrastando e soltando o **PickBranch** designer do **caixa de ferramentas** ou usando o menu de contexto dentro de **escolher** superfície de design. Para obter detalhes, consulte o [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tópico. Observe que o único item que pode ser colocado dentro de um **escolher** designer de atividade é uma **PickBranch** designer de atividade.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Escolha propriedades de atividade em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Pick> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Pick> no cabeçalho. O valor padrão é picareta. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|

## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
- [Escolher atividade](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Usando a atividade de Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)