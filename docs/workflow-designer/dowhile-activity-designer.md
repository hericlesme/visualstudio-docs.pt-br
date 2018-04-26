---
title: Designer de fluxo de trabalho - Designer de atividade DoWhile
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23588a044596ce5250cc68d01263f5d80775866a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="dowhile-activity-designer"></a>Designer de atividade DoWhile

O <xref:System.Activities.Statements.DoWhile> atividade executa a atividade contida em seu <xref:System.Activities.Statements.DoWhile.Body%2A> pelo menos uma vez, até que uma determinada condição for avaliada como **false**. Se você precisar a atividade contida em um corpo de loop para ser executado zero ou mais vezes, use a atividade de <xref:System.Activities.Statements.While> em vez disso.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriedades DoWhile em Designer de Fluxo de Trabalho

A tabela a seguir mostra o mais útil <xref:System.Activities.Statements.DoWhile> propriedades da atividade e descreve como usá-las no designer:

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|A atividade para executar enquanto a condição é **true**. Para adicionar o <xref:System.Activities.Statements.DoWhile.Body%2A> atividade, remover uma atividade da caixa de ferramentas para a **corpo** caixa o **DoWhile** designer de atividade com o texto da dica "Descartar atividade aqui".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|verdadeiro|A condição a ser avaliada após cada iteração do loop. Para definir o <xref:System.Activities.Statements.DoWhile.Condition%2A>, digite uma expressão do Visual Basic no **condição** caixa o **DoWhile** atividade designer ou na grade de propriedades.|

## <a name="see-also"></a>Consulte também

- [While](../workflow-designer/while-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)