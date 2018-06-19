---
title: 'Designer de fluxo de trabalho - como: definir pontos de interrupção em fluxos de trabalho (legados)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0c70b630404830fa8c733a7310e4700da8f08b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975189"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Como: Definir pontos de interrupção em fluxos de trabalho (o legados)

Este tópico descreve como definir pontos de interrupção no Windows Workflow Foundation (WF) usando o Designer de fluxo de trabalho do Windows herdados de compilação de aplicativos. Use o Designer de fluxo de trabalho herdados quando as necessidades de seu aplicativo do Windows Workflow Foundation direcionar o .NET Framework versão 3.5 ou o WinFX.

 Quando você usar o Designer de fluxo de trabalho herdados no Visual Studio 2010 para criar um aplicativo do Windows Workflow Foundation, você pode definir pontos de interrupção em c# e o código do Visual Basic, como você faria no Visual Studio. Como esperado, a execução de fluxo de trabalho que ele pare em cada ponto de interrupção esse definido.

 Um ponto de interrupção tem três estados: *pendente*, *associado*, e *erro*. Quando você definir um ponto de interrupção, ele está pendente, e ele é representado por um ícone oco vermelho. Quando o tempo de execução carregado o tipo de fluxo de trabalho, transformações e limite é representado por um ícone vermelho contínuo. Se você especificar um formato incorreto do ponto de interrupção, como um nome de atividade que não é válida, uma janela de erro aparece. O ponto de interrupção é adicionado ainda para a janela de ponto de interrupção, mas é marcado com um pequeno “x”.

 Você pode definir pontos de interrupção em uma atividade na superfície de design de fluxo de trabalho das seguintes maneiras:

-   A atividade e selecione **ponto de interrupção \ Inserir ponto de interrupção**.

-   Selecione a atividade e pressione F9.

-   Selecione **novo ponto de interrupção** do **depurar** menu.

     Você também pode usar esta opção para definir um novo ponto de interrupção a depuração, quando o depurador para em um ponto de interrupção.

    > [!NOTE]
    > Os pontos de interrupção em fluxos de trabalho chamados não são suportados.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Para definir um ponto de interrupção usando a nova opção de ponto de interrupção no menu debug

1.  Sobre o **depurar** menu, selecione **novo ponto de interrupção**.

2.  Clique em **interromper na função**.

     O **novo ponto de interrupção** caixa de diálogo é aberta.

3.  Especifique o nome de uma atividade no **função** caixa de texto usando a seguinte sintaxe: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.

    > [!NOTE]
    > Opcionalmente, em vez de usar o nome da atividade no **função** caixa de texto, você pode definir um ponto de interrupção, especificando o caminho absoluto da atividade de fluxo de trabalho. Por exemplo, suponha que você tiver uma solução de fluxo de trabalho chamada **WorkflowConsoleApplication1** e um fluxo de trabalho na solução chamada **Workflow1** que usa uma atividade chamada **Delay1**. Você pode usar o nome da atividade **Delay1** ou especifique o caminho como **Delay1:WorkflowConsoleApplication1.Workflow1** ou **Delay1:WorkflowConsoleApplication1.Workflow1: { 6614886A-608E-412B-BF98-99FF1559DDDF}**.

4.  Selecione o **usar o IntelliSense** caixa de seleção para verificar o nome da função.

     Se esta caixa de seleção não estiver selecionada, nenhuma verificação do nome do ponto de interrupção é executada.

5.  Selecione **fluxo de trabalho** do **idioma** lista.

6.  Clique em **OK**.

## <a name="see-also"></a>Consulte também

- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)
- [Invocando o depurador do Visual Studio para Windows Workflow Foundation (herdado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)