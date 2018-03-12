---
title: 'Como: depurar fluxos de trabalho baseados em ASP.NET (herdado) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: 3c62d4df23eb494d52a387da5e1727e4419f2ce8
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Como: Fluxos de trabalho de depuração ASP.NET-Based (legados)
Este tópico descreve como depurar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-com base em [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicativos voltados para o o [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] no Designer de fluxo de trabalho herdado do Windows.

 Você pode depurar fluxos de trabalho herdados que são iniciados no ASP.NET ou em fluxos de trabalho herdados que são publicados como um serviço Web anexando o processo no qual o fluxo de trabalho é hospedado.

### <a name="to-debug-an-aspnet-based-workflow"></a>Para depurar um fluxo de trabalho ASP.NET-based

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