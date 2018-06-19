---
title: Designer de fluxo de trabalho - Designer de atividade Rethrow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d441724afa1cf481bc15e2a43e6ec744a951187
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973830"
---
# <a name="rethrow-activity-designer"></a>Designer de atividade de Relançar

O **relançar** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Rethrow> atividade.

## <a name="the-rethrow-activity"></a>A atividade de Relançar
 A atividade de <xref:System.Activities.Statements.Rethrow> lança uma exceção lançada anteriormente. Esta atividade somente pode ser usada em um manipulador de <xref:System.Activities.Statements.Catch> na atividade de <xref:System.Activities.Statements.TryCatch> .

### <a name="using-the-rethrow-activity-designer"></a>Usando o designer de atividade de Relançar
 O **relançar** designer de atividade pode ser encontrado no **tratamento de erros** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia no lado esquerdo do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **relançar** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.Rethrow> atividade com um padrão **DisplayName** de Throw. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **relançar** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

### <a name="the-rethrow-properties"></a>As propriedades de Relançar
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Rethrow> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Rethrow> . O padrão é Relançar.|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)