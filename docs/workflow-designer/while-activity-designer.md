---
title: Designer de fluxo de trabalho - ao Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02f0e83f674378ca7f9297aedbeb580b4f2cad89
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973396"
---
# <a name="while-activity-designer"></a>Quando designer de atividades

O <xref:System.Activities.Statements.While> atividade executa a atividade contida em seu <xref:System.Activities.Statements.While.Body%2A> enquanto especificado <xref:System.Activities.Statements.While.Condition%2A> é avaliada como **true**. A atividade contida nunca pode executar. Se você desejar que a atividade contida a ser executada pelo menos uma vez, use a atividade de <xref:System.Activities.Statements.DoWhile> em vez disso.

## <a name="while-properties-in-workflow-designer"></a>Quando propriedades em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.While> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.While> no cabeçalho. O valor padrão é quando. O valor pode ser editado no **propriedades** janela ou diretamente no cabeçalho de designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contém a atividade seja executada enquanto o <xref:System.Activities.Statements.While.Condition%2A> é avaliada como **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|verdadeiro|Contém a expressão que é avaliada para determinar se a atividade de <xref:System.Activities.Statements.While.Body%2A> deve ser executado.|

## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)