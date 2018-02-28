---
title: 'Como: localizar qual DLL o programa falhou | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: df872ea52d716b4eaedc9414bc7234ba7c6294d3
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Como localizar em qual DLL o programa falhou
  
 Se houver falhas no aplicativo durante uma chamada a uma DLL do sistema ou o código de outra pessoa, você precisará descobrir qual DLL estava ativa quando a falha ocorreu. Se você tiver uma falha em uma DLL fora do seu próprio programa, você pode identificar o local usando o **módulos** janela.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para descobrir onde ocorreu uma falha usando a janela Módulos  
  
1.  Observe o endereço onde a falha ocorreu.

    Se o endereço não é exibido na mensagem de erro, você precisará usar métodos alternativos para identificar a DLL. Se você suspeitar de uma DLL do sistema, você pode [carregar símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) de servidores de símbolo Microsoft durante a depuração. Caso contrário, você precisará [criar um arquivo de despejo](../debugger/using-dump-files.md) com pilha informações em vez disso. Vários [ferramentas](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) estão disponíveis para criar arquivos de despejo.
  
2.  Sobre o **depurar** menu, escolha **Windows**e clique em **módulos**.  
  
3.  No **módulos** janela, localize a **endereço** coluna. Você poderá precisar usar a barra de rolagem para vê-la.  
  
4.  Clique o **endereço** botão na parte superior da coluna para classificar as DLLs por endereço.  
  
5.  Examine a lista classificada para localizar a DLL cujo intervalo de endereço contém o local da falha.  
  
6.  Examine o **nome** e **caminho** colunas para ver o nome da DLL e o caminho.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando projetos de DLL](../debugger/debugging-dll-projects.md)   
 [Como usar a janela Módulos](../debugger/how-to-use-the-modules-window.md)