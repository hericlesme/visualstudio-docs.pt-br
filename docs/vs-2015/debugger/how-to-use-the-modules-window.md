---
title: 'Como: usar a janela módulos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f7a5c71a95c0e4c366b7001a3adf86d5bacc9c8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464019"
---
# <a name="how-to-use-the-modules-window"></a>Como usar a janela Módulos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Exibir módulos, DLLs e executáveis no depurador](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-modules-window).  
  
OBSERVAÇÃO]
>  Esse recurso não está disponível para depuração do SQL ou script.  
  
 O **módulos** janela lista de DLLs e EXE que são usados pelo seu programa e mostra informações relevantes para cada um.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Para exibir a janela Módulos no modo de interrupção ou no modo de execução  
  
-   Sobre o **Debug** menu, escolha **Windows**e, em seguida, clique em **módulos**.  
  
     Por padrão, o **módulos** janela classifica os módulos pela ordem de carregamento. No entanto, você pode escolher classificar por qualquer coluna.  
  
### <a name="to-sort-by-any-column"></a>Para classificar por qualquer coluna  
  
-   Clique no botão na parte superior da coluna.  
  
     Você pode carregar símbolos ou especificar um caminho de símbolo a partir de **módulos** janela usando o menu de atalho.  
  
## <a name="loading-symbols"></a>Carregando símbolos  
 No **módulos** janela, você pode ver quais módulos têm símbolos de depuração carregados. Essas informações são exibidas na **Status do símbolo** coluna. Se o status for **loadingCannot ignorada localizar ou abrir o arquivo PDB**, ou **carregamento desabilitado pela configuração de inclusão/exclusão**, você pode direcionar o depurador para baixar os símbolos de símbolo públicos da Microsoft servidores ou carregar símbolos de um diretório de símbolo em seu computador. Para obter mais informações, consulte [especificar arquivos de símbolo (. PDB) e código-fonte](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Para carregar símbolos manualmente  
  
1.  No **módulos** janela, o botão direito do mouse, um módulo para o qual os símbolos não foram carregados.  
  
2.  Aponte para **carregar símbolos de** e, em seguida, clique em **servidores de símbolo Microsoft** ou **caminho de símbolo**.  
  
#### <a name="to-change-symbol-load-settings"></a>Para alterar as configurações de carregamento do símbolo  
  
1.  No **módulos** janela, clique com botão direito de qualquer módulo.  
  
2.  Clique em **configurações de símbolo**.  
  
     Agora você pode alterar as configurações de carregamento de símbolo, conforme descrito em [especificar locais de símbolo e o comportamento de carregamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). As alterações não terão efeito até você reiniciar a sessão de depuração.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Para alterar o comportamento de carregamento do símbolo para um módulo específico  
  
1.  No **módulos** janela, clique com botão direito do módulo.  
  
2.  Aponte para **configurações automáticas de carregamento de símbolo** e, em seguida, clique em **sempre carregar manualmente** ou **padrão**. As alterações não terão efeito até você reiniciar a sessão de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Interrupção da execução](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)





