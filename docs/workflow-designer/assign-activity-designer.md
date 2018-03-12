---
title: Atribuir o Designer de atividade | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 875a05866a85084b58236ab6bf918201d1848b1d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="assign-activity-designer"></a>Atribua o designer de atividades
O **atribuir** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Assign> atividade.

## <a name="the-assign-activity"></a>A atividade atribuir
 A atividade de <xref:System.Activities.Statements.Assign> atribui um valor a uma variável ou um argumento.

### <a name="using-the-assign-activity-designer"></a>Usando o designer de atividade atribuir
 O **atribuir** designer de atividade pode ser encontrado no **primitivos** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia (como alternativa, selecione **caixa de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **atribuir** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde nunca atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.Assign> atividade com um padrão **DisplayName** de atribuição. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **atribuir** designer de atividade ou o **DisplayName** caixa da grade de propriedade.

### <a name="the-assign-properties"></a>As propriedades atribuir
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Assign> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Assign> . O padrão é atribui. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.Assign.To%2A>|verdadeiro|A variável ou o argumento para que <xref:System.Activities.Statements.Assign.Value%2A> é atribuído. Isso deve ser um identificador válido Visual Basic. Para definir a propriedade, digite uma expressão do Visual Basic no **para** caixa o **atribuir** atividade designer ou na grade de propriedades.|
|<xref:System.Activities.Statements.Assign.Value%2A>|verdadeiro|O valor que é atribuído à variável. Para definir o <xref:System.Activities.Statements.Assign.Value%2A>, digite uma expressão do Visual Basic no **valor** caixa o **atribuir** atividade designer ou na grade de propriedades.|

## <a name="see-also"></a>Consulte também

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)