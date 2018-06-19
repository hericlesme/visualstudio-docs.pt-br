---
title: 'Designer de fluxo de trabalho - como: criar uma condição declarativa de regra (herdado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43b359040256788db240274f43f706b41f01d021
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977937"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Como: Crie uma condição declarativa de regra (o legados)

Este tópico descreve como declarar uma condição de regra usando o Designer de fluxo de trabalho herdado do Windows que tem como destino o .NET Framework versão 3.5 ou o WinFX.

Uma instrução de condição for avaliada como **True** ou **False**. Uma condição de regra declarativa é uma instrução de condição que é criada usando o [caixa de diálogo de Editor de condição de regra (herdado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e armazenados como XML com o fluxo de trabalho. Pode incluir os predicados que comparam o estado de fluxo de trabalho e a algebra booleano que combina vários predicados.

As condições declarativas de regras são usadas nas seguintes atividades de para fora da caixa do Windows Workflow Foundation:

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

## <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Para criar uma condição de regra declarativamente usando o editor de condição de regra

1.  A atividade **propriedades** janela, clique no **condição** propriedade ou **UntilCondition** propriedade, dependendo da atividade.

2.  Selecione **condição de regra declarativa** na lista para a propriedade.

3.  Expanda o **condição** ou **UntilCondition** propriedade.

4.  Clique o **ConditionName** propriedade.

5.  Clique o **ConditionName** reticências **[...]**  para abrir o **condição selecione** caixa de diálogo.

6.  Clique em **nova condição** para abrir o **Editor de condição de regra** caixa de diálogo.

7.  Digite a expressão para a condição de **condição** caixa de texto.

     Para obter informações sobre como criar expressões de condição, consulte [caixa de diálogo de Editor de condição de regra (herdado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8.  Quando tiver terminado de criar a expressão de condição, clique em **Okey** para fechar a caixa de diálogo e criar a condição de regra com um nome atribuído.

     O **condição selecione** caixa de diálogo é aberta.

     Para obter informações sobre como usar o **condição selecione** caixa de diálogo, consulte [selecione a caixa de diálogo condição (o legados)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Consulte também

- [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)
- [Usando o ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)
- [Usando a atividade de IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)
- [Usando a atividade de replicador](http://go.microsoft.com/fwlink?LinkID=65080)
- [Usando While atividade](http://go.microsoft.com/fwlink?LinkID=65091)
- [Caixa de diálogo Editor de Condição de Regra (herdado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)
- [Selecione a caixa de diálogo Condição (herdado)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [Usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009)