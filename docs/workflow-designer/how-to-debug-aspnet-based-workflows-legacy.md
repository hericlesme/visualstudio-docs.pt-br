---
title: 'Como: depurar fluxos de trabalho baseados em ASP.NET (herdado) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0eb248f04119f8f0ad70b9a09a4fb22c73399233
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Como: Fluxos de trabalho de depuração ASP.NET-Based (legados)
Este tópico descreve como depurar aplicativos baseadas em [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)][!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que direcionam [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  
  
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
 [Chamar o depurador do Visual Studio para Windows Workflow Foundation (legados)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Como: definir pontos de interrupção em fluxos de trabalho (legados)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)