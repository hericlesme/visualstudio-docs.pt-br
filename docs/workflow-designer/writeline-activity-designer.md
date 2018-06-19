---
title: Designer de fluxo de trabalho - Designer de atividade WriteLine
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0cfe187a77a956c9ebca2649b33dba9218f0fb4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975021"
---
# <a name="writeline-activity-designer"></a>Designer de atividade WriteLine

O **WriteLine** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.WriteLine> atividade.

## <a name="the-writeline-activity"></a>A atividade WriteLine

Grava de atividade de <xref:System.Activities.Statements.WriteLine> texto a <xref:System.IO.TextWriter> um objeto especificado. Se nenhum <xref:System.IO.TextWriter> é especificado, <xref:System.Activities.Statements.WriteLine> grava o texto no console.

### <a name="using-the-writeline-activity-designer"></a>Usando o designer de atividade WriteLine
 O **WriteLine** designer de atividade pode ser encontrado no **primitivos** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **WriteLine** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.WriteLine> com <xref:System.Activities.Activity.DisplayName%2A> padrão WriteLine. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **WriteLine** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

### <a name="the-writeline-properties"></a>As propriedades WriteLine
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.WriteLine> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e algumas delas podem ser editadas na superfície de fluxo de trabalho Designerdesigner.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.WriteLine> . O padrão é WriteLine. Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é prática recomendada usar esse.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|O texto a gravação. Para definir a propriedade, digite uma expressão do Visual Basic no **texto** caixa o **WriteLine** atividade designer ou na grade de propriedades.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> a <xref:System.Activities.Statements.WriteLine> que grava <xref:System.Activities.Statements.WriteLine.Text%2A>. O padrão é o console.|

## <a name="see-also"></a>Consulte também

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [atribuir](../workflow-designer/assign-activity-designer.md)
- [atraso](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)