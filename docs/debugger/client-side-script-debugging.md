---
title: "Depuração de Script do lado do cliente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 401ee40e2d296cbef041cb56568b639d05835f04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="client-side-script-debugging"></a>Depuração de script do lado do cliente
O depurador do Visual Studio fornece um ambiente de depuração abrangente para localizar e corrigir erros em scripts do lado do cliente em páginas ASP.NET.  
  
## <a name="opening-script-documents"></a>Abrindo Documentos de Script  
 Você pode ver a lista de documentos de script do lado do servidor e cliente no **Solution Explorer** para exibir. Você pode abrir qualquer documento de script de **Gerenciador de soluções**. Para obter mais informações, consulte [como: exibir documentos de Script](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mapeamento de ponto de interrupção  
 No Visual Studio, você não pode depurar diretamente o código do lado do servidor, mas pode definir um ponto de interrupção em um arquivo do lado do servidor. O Visual Studio automaticamente mapeia o ponto de interrupção em um local correspondente no arquivo do cliente e cria um ponto de interrupção mapeado no código do cliente.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Anexar a script manual ou automaticamente  
 Para iniciar a depuração de script no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], o depurador deve anexar o script que você deseja depurar. Isso pode acontecer manualmente ou automaticamente.  
  
 Você pode anexar manualmente usando a interface do depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para escolher um processo em execução do script ao qual você deseja anexar. Para obter mais informações, consulte [como: anexar ao Script](../debugger/how-to-attach-to-script.md).  
  
 O depurador é anexado automaticamente ao script quando uma das situações ocorrer:  
  
-   Você atinge um conjunto de pontos de interrupção no script.  
  
-   Você atinge uma declaração de `Stop` do VBScript ou uma declaração de `debugger` do JScript no seu código de script.  
  
-   O navegador ou servidor encontra um erro de sintaxe ou de tempo de execução em seu script. Quando isso ocorre, uma caixa de diálogo aparecerá e terá a opção de iniciar a depuração.  
  
 Ao anexar manualmente ao script, o processo de script continuará a ser executado até que seja paralisado de alguma maneira. Pode pará-lo escolhendo **quebra** no **depurar** menu.  
  
 Quando o depurador é anexado automaticamente, a execução de script é interrompida na linha onde o ponto de interrupção, instrução de `Stop` ou de `debugger`, ou erro ocorreu, ou no ponto onde você escolher para iniciar a depuração no Internet Explorer.  
  
 Nesse ponto, você pode usar recursos normais do depurador para iniciar a depuração. Por exemplo, você pode usar **etapa** comandos para continuar a executar o código linha por linha. Você pode usar o **pilha de chamadas** janela para visualizar e controlar o fluxo do script. Você pode usar as janelas de variáveis ou **imediato** janela para exibir ou alterar as propriedades e variáveis.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Mensagens de erro aprimoradas para depuração de scripts  
 Visual Studio fornece mensagens de erro aprimorada para problemas de depuração de script comuns. Essas mensagens não aparecem a menos que você anexe ao Internet Explorer manualmente. Se você encontrar uma condição de erro quando o Internet Explorer for aberto automaticamente, tente anexar de forma manual para poder ver as mensagens de erro.  
  
## <a name="debugging-ajax-script-applications"></a>Depurando aplicativos de script AJAX  
 Os aplicativos da Web com AJAX ativado fazem uso intenso de códigos de script e desafios especiais de depuração de representação. Para obter mais informações sobre técnicas de depuração AJAX, consulte  
  
 [Depuração e rastreamento de visão geral de aplicativos Ajax](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Limitações na depuração de Script](../debugger/limitations-on-script-debugging.md)   
 [Janelas variáveis](../debugger/debugger-windows.md)   
 [Janela Imediata](../ide/reference/immediate-window.md)   
 [Visão geral de aplicativos Ajax de rastreamento e depuração](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)