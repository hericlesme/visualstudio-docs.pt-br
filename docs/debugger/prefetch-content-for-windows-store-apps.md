---
title: Depurar usando a pré-busca de conteúdo em aplicativos UWP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 241937c8462577d6af375d2440efe828a738a8cc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Depurar aplicativos UWP usando pré-busca de conteúdo do Visual Studio
  
 Para tornar seu aplicativo UWP mais responsivo, você pode solicitar ao Windows para pré-carregar algum conteúdo da web, como imagens, ou páginas da web para o aplicativo [WinINet](http://msdn.microsoft.com/library/0a06f2af-957a-4dff-a8cc-187370181b5c) cache. Essa funcionalidade chama-se pré-busca. É especialmente eficiente para o conteúdo que é usado na inicialização, mas você pode executar a pré-busca de outro conteúdo usado frequentemente, muito. Os métodos de [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) classe permite especificar os URIs do conteúdo que você deseja pré-carregar. Consulte o SDK do Windows [amostra de pré-busca de conteúdo](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) para obter exemplos de como adicionar a funcionalidade ContentPrefetcher ao seu aplicativo.  
  
 O Windows usa heurística para determinar quando e se a pré-busca deve ocorrer e quais recursos serão baixados. A heurística leva em conta condições de energia e rede do sistema da conta, o histórico de uso do aplicativo do usuário e os resultados das tentativas anteriores de pré-busca. No Visual Studio, você pode usar o **pré-busca de aplicativo de armazenamento do Windows gatilho** comando para forçar o Windows a ignorar a heurística ContentPrefetcher e pré-carregar todo o conteúdo da web especificado. Isso pode ser útil se você quiser testar o comportamento ou desempenho do aplicativo com o conteúdo para pré-buscar em um estado conhecido (carregado ou não carregado).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forçar o pré-carregamento dos recursos especificados do ContentPrefetcher  
 Este procedimento presume que você já definiu a funcionalidade ContentPrefetcher e especificou os URIs de conteúdo para pré-carregar em seu projeto de aplicativo. Para forçar o pré-carregamento de conteúdo quando os recursos especificados são novos ou modificados, você precisa iniciar e parar o aplicativo antes de escolher o **pré-busca de aplicativo de armazenamento do Windows gatilho** comando. Você executa o aplicativo primeiro para registrar os URIs. **Acionar pré-busca do Windows Store App** comando força o ContentPrefetcher a baixar o conteúdo e adicioná-lo ao cache. Nas execuções subsequentes do aplicativo, você pode presumir que o conteúdo esteja pré-carregado.  
  
1.  Inicie o aplicativo para registrar os URIs de conteúdo para pré-busca com o aplicativo. Sobre o **depurar** menu, escolha **iniciar depuração** (atalho de teclado: F5).  
  
2.  Sobre o **depurar** menu, escolha **parar depuração** (atalho de teclado: Shift + F5).  
  
3.  Sobre o **depurar** menu, escolha **outros destinos de depuração** e, em seguida, escolha **pré-busca de aplicativo de armazenamento do Windows gatilho**.  
  
 Agora você pode depurar, testar ou analisar seu aplicativo com os recursos Web pré-buscados.  
  
> [!NOTE]
>  Repita estas etapas sempre que adicionarem ou modificar o conteúdo da Web especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Postagem do blog: acionar pré-busca de aplicativos da Windows Store no Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)