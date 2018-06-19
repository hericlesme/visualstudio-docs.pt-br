---
title: Designer de fluxo de trabalho - Designer de atividade paralela
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2315c27bc0a35ac1dc839b5fd98003105d92bd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977225"
---
# <a name="parallel-activity-designer"></a>Designer paralelo de atividades

A atividade de <xref:System.Activities.Statements.Parallel> executa uma coleção de filhos atividades simultaneamente.

## <a name="the-parallel-activity"></a>A atividade paralela

A atividade de <xref:System.Activities.Statements.Parallel> armazena as atividades filho em uma coleção de <xref:System.Activities.Statements.Parallel.Branches%2A> . Use a atividade de <xref:System.Activities.Statements.Parallel> em vez de atividade de <xref:System.Activities.Statements.Sequence> se algumas das atividades filho podem ir ociosa.

O <xref:System.Activities.Statements.Parallel> atividade tem um <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> propriedade que contém um usuário especificado a expressão do Visual Basic. A atividade de <xref:System.Activities.Statements.Parallel> avalia essa propriedade após cada ramificação completa. Se ele for avaliada como **True**, em seguida, o <xref:System.Activities.Statements.Parallel> conclusão sem executar as outras ramificações da atividade. Se o <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> não é avaliada como **True**, em seguida, o <xref:System.Activities.Statements.Parallel> atividade é concluída quando todas as suas atividades filho forem concluídas.

### <a name="using-the-parallel-activity-designer"></a>Usando o designer paralelo de atividades

O **paralela** designer de atividade pode ser encontrado no **fluxo de controle** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia no lado esquerdo do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

O **paralela** designer de atividades pode ser arrastado o **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que os designers de atividade normalmente são colocadas, por exemplo, dentro de um **Sequência** designer de atividade. Depois de descartá-lo no Designer de fluxo de trabalho, ele cria um <xref:System.Activities.Statements.Parallel> atividade, que, por padrão, contém um <xref:System.Activities.Activity.DisplayName%2A> de **paralela**

Para adicionar uma atividade para o <xref:System.Activities.Statements.Parallel.Branches%2A> coleção de atividade paralela, arraste alguns outros designer de atividade do **caixa de ferramentas** e solte-o triângulo dentro a **paralela** designer de atividade. Os triângulos flanqueiam as atividades contidas em ramificações. As atividades adicionais podem ser adicionadas repetindo este procedimento. As atividades podem ser reordenadas arrastando e soltando dentro de **paralela** designer de atividade.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propriedades paralelas de atividade em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades paralelas de atividade e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável para exibição do designer de atividade no cabeçalho. O valor padrão é **paralela**. O valor pode ser editado no opcionalmente o **propriedades** grade ou diretamente no cabeçalho de designer de atividade.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|verdadeiro|Contém a coleção de atividades filhos sejam executadas.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Avaliado após uma ramificação completa. Se ele for avaliada como **True**, em seguida, agendados pendentes ramificações são canceladas. Se essa propriedade não está definida ou é avaliada como **False**, a atividade é concluída quando todas as suas atividades filho forem concluídas. O valor padrão é **nulo**.|

## <a name="see-also"></a>Consulte também

- [sequência](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)