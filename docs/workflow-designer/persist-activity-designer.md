---
title: Designer de fluxo de trabalho - persistir o Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04c7989f5cc37ec295f9fa778f2120dd372fd99a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="persist-activity-designer"></a>Persistir o designer de atividades

O **Persist** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Persist> atividade.

## <a name="the-persist-activity"></a>A atividade persistir

A atividade de <xref:System.Activities.Statements.Persist> salva um fluxo de trabalho em disco, se possível. A atividade de <xref:System.Activities.Statements.Persist> não pode ser executada em uma zona de não persistência como, por exemplo, em uma atividade de <xref:System.Activities.Statements.TransactionScope> . Se você usar uma atividade de <xref:System.Activities.Statements.Persist> em um escopo de não persistência, uma exceção é lançada em tempo de execução.

### <a name="using-the-persist-activity-designer"></a>Usando o designer de atividade de persistir

O **Persist** designer de atividade pode ser encontrado no **tempo de execução** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas** guia (como alternativa, selecione **caixa de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

O **Persist** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.Persist> atividade com um padrão **DisplayName** de persistência. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **Persist** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

### <a name="the-persist-properties"></a>As propriedades persistir

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Persist> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e algumas delas podem ser editadas na superfície do Designer de fluxo de trabalho.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Persist> . O padrão é persiste. Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|

## <a name="see-also"></a>Consulte também

- [Tempo de execução](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)