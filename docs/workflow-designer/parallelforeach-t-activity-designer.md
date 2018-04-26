---
title: Designer de fluxo de trabalho - ParallelForEach&lt;T&gt; Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd7d3220bc67b764b96033ad516eb857bec6014
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="parallelforeach-activity-designer"></a>Designer de atividade ParallelForEach

A atividade de <xref:System.Activities.Statements.ParallelForEach%601> enumera os elementos de uma coleção e executa uma declaração inserido para cada elemento da coleção paralelamente, que está de forma assíncrona no mesmo segmento. Use esta atividade do controle de fluxo em vez de atividade de <xref:System.Activities.Statements.Sequence> se as atividades filhos desta atividade são esperadas ir ociosa.

O <xref:System.Activities.Statements.ParallelForEach%601> atividade tem um <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> propriedade que contém um usuário especificado a expressão do Visual Basic. A atividade de <xref:System.Activities.Statements.ParallelForEach%601> avalia essa propriedade após cada ramificação completa. Se ele for avaliada como **true**, em seguida, o <xref:System.Activities.Statements.ParallelForEach%601> conclusão sem executar as outras ramificações da atividade. Se o <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> não é avaliada como **true**, em seguida, o <xref:System.Activities.Statements.ParallelForEach%601> atividade é concluída quando todas as suas atividades filho forem concluídas.

## <a name="the-parallelforeacht-activity"></a>O ParallelForEach < T\> atividade

<xref:System.Activities.Statements.ParallelForEach%601> enumera os valores e agendamento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> para cada valor que enumera sobre. Agenda somente <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Como o corpo executa depende se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> vai ociosa.

Se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> não vai ociosa, executa em uma ordem inversa como as atividades agendados são tratadas como uma pilha, a atividade agendada a última executa primeiro. Por exemplo, se você tiver uma coleção de {1,2,3,4}na <xref:System.Activities.Statements.ParallelForEach%601> e usar um **WriteLine** como o corpo para gravar o valor. Você tem 4, 3, 2, 1 - out impresso no console. Isso ocorre porque **WriteLine** não vai ocioso isso após 4 **WriteLine** atividades foram agendadas, elas executadas usando um comportamento de pilha (primeiro no último out).

Mas se você tiver atividades em <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> que pode ir ociosa, como uma atividade de <xref:System.ServiceModel.Activities.Receive> ou a atividade de <xref:System.Activities.Statements.Delay> . Em seguida não há necessidade de esperar que eles terminem concluir. <xref:System.Activities.Statements.ParallelForEach%601> vá para a atividade e tente agendados seguintes corpo de executá-lo. Se a atividade ociosa vai além disso, <xref:System.Activities.Statements.ParallelForEach%601> move novamente em atividade de corpo seguir.

### <a name="using-the-parallelforeacht-activity-designer"></a>Usando o ParallelForEach\<T > Designer de atividade

O **ParallelForEach\<T >** designer de atividade pode ser encontrado no **fluxo de controle** categoria do **caixa de ferramentas**, que é acessado clicando o  **Caixa de ferramentas** guia no lado esquerdo do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

O **ParallelForEach\<T >** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que os designers de atividade normalmente são colocadas, para exemplo, dentro de um **sequência** designer de atividade. Depois de descartá-lo no Designer de fluxo de trabalho, ele cria um <xref:System.Activities.Statements.ParallelForEach%601> atividade, que, por padrão, contém um <xref:System.Activities.Activity.DisplayName%2A> de **ParallelForEach < Int32\>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\> propriedades no Designer de fluxo de trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ParallelForEach%601> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável para exibição do designer de atividade no cabeçalho. O valor padrão é **ParallelForEach\<Int32 >**. O valor pode ser editado no opcionalmente o **propriedades** grade ou diretamente no cabeçalho de designer de atividade.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|A atividade a executar para cada item na coleção. Para adicionar o <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> atividade, remover uma atividade da caixa de ferramentas para a **corpo** caixa o **ParallelForEach\<T >** designer de atividade com o texto da dica "Descartar atividade aqui".|
|**TypeArgument**|verdadeiro|O tipo dos itens a <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> coleção especificada pelo parâmetro genérico *T*. Por padrão, **TypeArgument** é definido como **Int32**. Para alterar o tipo T no **ParallelForEach < T\>**  designer de atividade, alterar o valor da **TypeArgument** caixa de combinação na grade de propriedades.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|verdadeiro|A coleção de itens para iterar. Para definir o <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, digite uma expressão do Visual Basic no **valores** caixa o **ForEach < T\>**  designer de atividade na caixa com o texto da dica "Inserir uma expressão do VB" ou em  **Valores** caixa o **propriedades** janela.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Avaliado após cada iteração completa. Se avalia para retificar, então o agendada durante iterações é cancelado. Se esta propriedade não for definida, todas as instruções agendados executam até a conclusão.|

Por padrão, o iterador do loop é chamado item. Você pode alterar o nome da variável de iterador no **ForEach** caixa **ParallelForEach\<T >** designer de atividade. O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ParallelForEach%601> .

## <a name="see-also"></a>Consulte também

- [sequência](../workflow-designer/sequence-activity-designer.md)
- [Paralelo](../workflow-designer/parallel-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)