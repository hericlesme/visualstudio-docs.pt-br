---
title: Designer de fluxo de trabalho - Designer de sequência de atividades
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e72c5b5e43ca037a6d65e3e4980fdb0f89f000f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31972036"
---
# <a name="sequence-activity-designer"></a>Arranje seqüencialmente o designer de atividades

A atividade de <xref:System.Activities.Statements.Sequence> contém uma coleção ordenada de atividades filhos que executa em ordem.

Outra maneira de executar um conjunto de atividades em ordem é usar uma atividade de <xref:System.Activities.Statements.Flowchart> . Considere o uso de [fluxograma](../workflow-designer/flowchart-activity-designer.md) quando você tiver uma ramificação simples ou fluxo de programa que você deseja modelar diagrammatically em loop.

## <a name="using-the-sequence-activity-designer"></a>Usando o designer de atividade de sequência

Para adicionar um <xref:System.Activities.Statements.Sequence> atividade, arraste o **sequência** designer de atividade do **caixa de ferramentas** e solte-o na superfície de Designer de fluxo de trabalho do Windows. Para adicionar uma atividade filho a este <xref:System.Activities.Statements.Sequence> atividade, arraste algumas outras atividades do **caixa de ferramentas** e solte-o triângulo na caixa com o texto da dica "Descartar atividade aqui".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade da sequência em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Sequence> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Sequence> no cabeçalho. O valor padrão é sequência. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|

## <a name="see-also"></a>Consulte também

- [Fluxograma](../workflow-designer/flowchart-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)