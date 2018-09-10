---
title: Exibir as DLLs e executáveis no depurador | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f582c435239c83503b179d6bb5e142936a41cb4b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279005"
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Exibir as DLLs e executáveis usando a janela de módulos no depurador do Visual Studio
 
O **módulos** janela lista de DLLs e executáveis (EXE) que são usados pelo seu programa e mostra informações relevantes para cada um. 

> [!NOTE]
>  Esse recurso não está disponível para depuração do SQL ou script. 
  
### <a name="to-display-the-modules-window"></a>Para exibir a janela módulos  
  
-   Enquanto você estiver depurando, selecione **Depurar > Windows** e, em seguida, clique em **módulos**.  
  
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
 [Interrupção da execução](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)