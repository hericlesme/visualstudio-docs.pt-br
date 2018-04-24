---
title: Exibir DLLs e executáveis no depurador | Microsoft Docs
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
ms.openlocfilehash: 46dc913b95396e16f208611bcfc926378609bef6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Exibir DLLs e executáveis usando a janela de módulos no depurador do Visual Studio
 
O **módulos** janela lista de DLLs e executáveis (EXE) que são usados pelo seu programa e mostra informações relevantes para cada um. 

> [!NOTE]
>  Esse recurso não está disponível para depuração do SQL ou script. 
  
### <a name="to-display-the-modules-window"></a>Para exibir a janela módulos  
  
-   Enquanto você está depurando, selecione **Depurar > Windows** e, em seguida, clique em **módulos**.  
  
     Por padrão, o **módulos** janela classifica módulos por ordem de carregamento. No entanto, você pode escolher classificar por qualquer coluna.  
  
### <a name="to-sort-by-any-column"></a>Para classificar por qualquer coluna  
  
-   Clique no botão na parte superior da coluna.  
  
     Você pode carregar símbolos ou especificar um caminho de símbolo a partir de **módulos** janela usando o menu de atalho.  
  
## <a name="loading-symbols"></a>Carregando símbolos  
 No **módulos** janela, você pode ver quais módulos têm símbolos carregados de depuração. Essas informações aparecem no **Status símbolo** coluna. Se o status for **loadingCannot ignorados localizar ou abrir o arquivo PDB**, ou **carregamento desabilitado pela configuração de inclusão/exclusão**, você pode direcionar o depurador para baixar os símbolos do símbolo público Microsoft servidores ou ao carregar os símbolos de um diretório de símbolo em seu computador. Para obter mais informações, consulte [especificar símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Para carregar símbolos manualmente  
  
1.  No **módulos** janela, com o botão direito, um módulo para o qual símbolos não foram carregados.  
  
2.  Aponte para **carregar símbolos de** e, em seguida, clique em **Microsoft Symbol Servers** ou **caminho de símbolo**.  
  
#### <a name="to-change-symbol-load-settings"></a>Para alterar as configurações de carregamento do símbolo  
  
1.  No **módulos** janela, clique com botão direito qualquer módulo.  
  
2.  Clique em **configurações de símbolo**.  
  
     Agora, você pode alterar as configurações de carga de símbolo, conforme descrito em [Especifique locais de símbolo e o comportamento de carregamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). As alterações não terão efeito até você reiniciar a sessão de depuração.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Para alterar o comportamento de carregamento do símbolo para um módulo específico  
  
1.  No **módulos** janela, clique com botão direito do módulo.  
  
2.  Aponte para **configurações automáticas de carga de símbolo** e, em seguida, clique em **sempre carregar manualmente** ou **padrão**. As alterações não terão efeito até você reiniciar a sessão de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Interrompendo a execução](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especifique o símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)