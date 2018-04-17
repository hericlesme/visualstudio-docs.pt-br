---
title: Caixa de diálogo Editor de condição de regra (herdado) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62b74956dc12e19a5594585e8d356b77ae5549b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Regra a caixa de diálogo editor de condição (o legados)

Este tópico descreve como usar o **Editor de condição de regra** caixa de diálogo no Designer de fluxo de trabalho herdado do Windows. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

Criar e modificar condições declarativas de regra usando o **Editor de condição de regra** caixa de diálogo. Essas condições de regras são expostas como propriedades nas seguintes atividades de para fora da caixa do Windows Workflow Foundation:

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

Você acessa o **Editor de condição de regra** caixa de diálogo usando o [selecione a caixa de diálogo condição (o legados)](../workflow-designer/select-condition-dialog-box-legacy.md).

A tabela a seguir descreve os elementos de interface de usuário do **Editor de condição de regra** caixa de diálogo.

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Condição:**|Insira a expressão para a condição de regra.|
|**OK**|Clique para salvar a condição de regra.|

## <a name="entering-condition-expressions"></a>Inserindo expressões de condição

Expressões de condição estão inseridos como texto. Você pode digitar **isso.** para o editor para fazer referência a campos, propriedades e métodos usados no fluxo de trabalho, usando um menu como IntelliSense. Ou você pode digitar um nome de membro de fluxo de trabalho diretamente. Você pode adicionar operadores lógicos a condição, como AND, OU, e NOT. Você também pode adicionar predicados. Um predicado é um operador binário e dois operandos. Os operadores binários com suporte são **==**, **>**, **\<**, **>=**, e **<=**. Os operandos são suportados valor constante, função aritmética, e membros públicos o escopo.

Você pode especificar o tipo de comparação, e você pode comparar e **nulo** ou uma cadeia de caracteres vazia. Você pode fazer chamadas aninhados aos membros em uma variável que contém um tipo complexo, por exemplo, `this.Address.State == "WA"`.

O editor de condição de regra oferece suporte aos seguintes operadores:

-   Operadores relacionais: ==, =! =

-   Operadores de comparação: <, \<=, >, > =

-   Operadores aritméticos: +, -, \*, /, MOD

-   Operadores lógicos: E, & &, OR, &#124; &#124;, não,!

-   Operadores bit a bit: &,&#124;

Precedência de operadores de expressão segue regras de precedência de operador C#.

O editor de condição de regra suporta as seguintes expressões numéricas:

== 1D de this.i (resoluções a 1,0)

== 1E1 de this.i (resoluções a 10,0)

== 1L de this.i (resoluções como um longo)

== 1M de this.i (resoluções como um decimal)

== 1F de this.i (resoluções como um único)

== 1U de this.i (resoluções como um unsigned int)

Para obter mais informações sobre condições, consulte [usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Consulte também

- [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)
- [Selecione a caixa de diálogo Condição (herdado)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [Usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009)
- [Designer herdado para a ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)