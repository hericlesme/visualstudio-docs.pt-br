---
title: Novidades no depurador no Visual Studio de 2017 | Microsoft Docs
ms.custom: 
ms.date: 03/07/2016
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
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: "81"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a08c56ae60822e6d4183e5789c68cbe383b4dd5
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Novidades do depurador[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

O depurador inclui os seguintes recursos novos:

- Novo no 15,5, o **instantâneo depurador** tira um instantâneo de seus aplicativos em produção quando executa código que você está interessado. Para instruir o depurador para obter um instantâneo, você defina snappoints e logpoints no seu código. O depurador permite que você veja exatamente o que deu errado, sem afetar o tráfego do seu aplicativo de produção. O depurador de instantâneo pode ajudá-lo a reduzir drasticamente o tempo necessário para resolver problemas que ocorrem em ambientes de produção.

    Coleção de instantâneo está disponível para os seguintes aplicativos web em execução no serviço de aplicativo do Azure:

    * Aplicativos ASP.NET em execução no .NET Framework 4.6.1 ou posterior.
    * Aplicativos do ASP.NET Core em execução no .NET Core 2.0 ou posterior no Windows.

    Para obter mais informações, consulte [depurar aplicativos do ASP.NET ao vivo usando o depurador do instantâneo](../debugger/debug-live-azure-applications.md).

- Novo no 15,5 somente no Visual Studio Enterprise **IntelliTrace etapa-back** automaticamente tira um instantâneo do seu aplicativo em cada ponto de interrupção e o depurador de evento da etapa. Os instantâneos gravados permitem que você volte para os pontos de interrupção anteriores ou etapas e exibir o estado do aplicativo como ele era no passado. IntelliTrace back etapa pode economizar tempo quando você deseja ver o estado anterior do aplicativo, mas não deseja reiniciar a depuração ou recriar o estado do aplicativo desejado.

    Você pode navegar e exibir instantâneos usando o **com versões anteriores do etapa** e **Avançar** botões na barra de ferramentas Depurar. Esses botões navegar os eventos que aparecem no **eventos** guia o **ferramentas de diagnóstico** janela.

    ![Etapa para trás e frente botões](../debugger/media/intellitrace-step-back-icons-description.png  "botões etapa com versões anteriores e Avançar")

    Para obter mais informações, consulte o [exibir instantâneos usando IntelliTrace etapa-back](../debugger/how-to-use-intellitrace-step-back.md) página.

- O **auxiliar de exceção** substitui o Assistente de exceção e aparece em uma caixa de diálogo não modal onde ocorreu o erro. O **auxiliar de exceção** fornece acesso mais rápido para quaisquer exceções internas, a análise adicional pelo depurador (se disponível) e acesso imediato ao **configurações de exceção** para a exceção. O auxiliar de exceção também podem ser arrastado para um modo de exibição flutuante se ele está bloqueando algo que você precisa ver.

    Por exemplo, um **NullReferenceException** agora mostra a variável que tenha a referência nula (informações adicionais).

    ![Auxiliar de exceção do depurador](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Para obter mais informações, consulte a postagem de blog [Usando o novo Auxiliar de Exceção no Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

- Agora você pode executar para uma linha de código enquanto está em pausa no depurador, selecionando o **execução aqui** ícone de seta verde (você verá o ícone ao passar o mouse sobre uma linha de código). Isso elimina a necessidade de definir pontos de interrupção temporários.

    ![Depurador do executado para clique](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- Você pode definir condições de exceções no **configurações de exceção** caixa de diálogo (você pode fazer isso usando o **Editar condição** ícone na caixa de diálogo Configurações de exceção ou usando o menu do botão direito do mouse na exceção). Condições atualmente com suporte incluem os nomes de módulo para incluir ou excluir da exceção.

    ![Condições em uma exceção](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Anexe ao processo de caixa de diálogo inclui um novo recurso de pesquisa que pode ajudá-lo mais a identificar rapidamente o que você precisa anexar ao processo.

    ![Pesquisar em Anexar ao processo](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

Para obter mais informações sobre esses novos recursos, consulte o [notas de versão do [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/index.md)  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)