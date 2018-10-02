---
title: Como fazer referência a informações de símbolo do Windows | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 385b9e4511c44c02a358eb88471cd8369971ed1c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475579"
---
# <a name="how-to-reference-windows-symbol-information"></a>Como fazer referência a informações de símbolo do Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: informações de símbolo do Windows de referência](https://docs.microsoft.com/visualstudio/profiling/how-to-reference-windows-symbol-information).  
  
As Ferramentas de Criação de Perfil do Visual Studio usam arquivos de símbolo (.pdb) para resolver nomes simbólicos como nomes de função em binários de programa. Siga estas etapas para baixar automaticamente e atualizar os arquivos .pdb corretos para a versão do Windows no computador local.  
  
> [!NOTE]
>  Essa configuração não afeta os relatórios existentes. Somente os relatórios criados após especificar o servidor de símbolo terão as informações de símbolo.  
  
 Para obter mais informações, consulte [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Para usar o servidor de símbolos da Microsoft  
  
1.  Crie uma pasta para conter as informações de arquivo de símbolo, como C:\SymbolCache.  
  
2.  No menu **Ferramentas**, clique em **Opções**.  
  
     A caixa de diálogo **Opções** é exibida.  
  
3.  Expanda a árvore **Depuração** e, em seguida, clique em **Símbolos**.  
  
4.  Em **Locais do arquivo de símbolo (.pdb)**, selecione **Servidores de Símbolos da Microsoft**  
  
5.  Em **Armazenar em cache os símbolos do servidor de símbolos para este diretório**, digite o caminho da pasta que foi criada na etapa 1, por exemplo:  
  
     **C:\SymbolCache**  
  
     Você também pode clicar no botão de reticências (**...** ) e, em seguida, selecionar um diretório na caixa de diálogo **Procurar Pasta**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Como serializar informações de símbolo](../profiling/how-to-serialize-symbol-information.md)



