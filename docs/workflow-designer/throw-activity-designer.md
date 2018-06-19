---
title: Designer de fluxo de trabalho - Designer de atividade Throw
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bb94ad17b78b1264129b8a5ba00a964edbd2f2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974650"
---
# <a name="throw-activity-designer"></a>Lance o designer de atividades

O **gerar** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Throw> atividade.

## <a name="the-throw-activity"></a>A atividade throw
 A atividade de <xref:System.Activities.Statements.Throw> gerencie uma exceção.

### <a name="using-the-throw-activity-designer"></a>Usando o designer de atividade throw
 O **gerar** designer de atividade pode ser encontrado no **tratamento de erros** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia no lado esquerdo do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **gerar** designer de atividades pode ser arrastado o **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.Throw> atividade com um padrão **DisplayName** de Throw. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **lançar** designer de atividade ou o **DisplayName** caixa da grade de propriedade. A propriedade de <xref:System.Activities.Statements.Throw.Exception%2A> deve ser editada na grade de propriedade.

### <a name="the-throw-properties"></a>As propriedades throw
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Throw> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Throw> . O padrão é throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|verdadeiro|A exceção para lançar. Esta exceção deve derivar de <xref:System.Exception>. Para especificar a exceção, digite uma expressão do Visual Basic na grade de propriedade.|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [relançar](../workflow-designer/rethrow-activity-designer.md)
- [Designer de atividade Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)