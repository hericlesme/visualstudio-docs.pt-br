---
title: 'Designer de fluxo de trabalho - como: depurar fluxos de trabalho baseados em ASP.NET (legados)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7bf16a6a88c5d4cd063f1c32ca846031d8b2588d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Como: Fluxos de trabalho de depuração ASP.NET-Based (legados)

Este tópico descreve como depurar aplicativos ASP.NET baseado em Windows Workflow Foundation (WF) que visam o .NET Framework versão 3.5 ou WinFX no Designer de fluxo de trabalho herdado do Windows.

Você pode depurar fluxos de trabalho herdados que são iniciados no ASP.NET ou em fluxos de trabalho herdados que são publicados como um serviço Web anexando o processo no qual o fluxo de trabalho é hospedado.

## <a name="to-debug-an-aspnet-based-workflow"></a>Para depurar um fluxo de trabalho ASP.NET-based

1.  Habilitar a depuração para o aplicativo ASP.NET definindo **debug = true** no arquivo Web. config.

2.  Defina a biblioteca de fluxo de trabalho como o projeto de inicialização, e pontos de interrupção no fluxo de trabalho.

3.  Insira a URL da página da Web padrão nas propriedades do projeto de fluxo de trabalho **depurar** opção **Iniciar navegador com URL externa** caixa de texto.

4.  Selecione **anexar ao processo** no **depurar** menu.

5.  Selecione o processo para anexar a partir de **processos disponíveis** lista.

     Para anexar w3wp.exe, ao webdev.webserver, ou o processo de aspnet_wp em que o fluxo de trabalho é hospedado.

6.  Clique em **selecione** lado a **anexar para** caixa de texto.

     O **Selecionar tipo de código** caixa de diálogo é exibida.

7.  Selecione **depurar esses tipos de código** e selecione **fluxo de trabalho**.

8.  Clique em **OK**.

9. Clique em **Anexar**.

10. Abra a página da Web padrão em um navegador e inicie o fluxo de trabalho.

## <a name="see-also"></a>Consulte também

- [Invocando o depurador do Visual Studio para Windows Workflow Foundation (herdado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Como definir pontos de interrupção em fluxos de trabalho (herdado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)