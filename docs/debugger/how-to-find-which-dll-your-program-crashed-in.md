---
title: 'Como: localizar qual DLL o programa falhou | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.dll
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
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95ad4f9c028b9b40bf5104539a608453c9d6f9dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Como localizar em qual DLL o programa falhou
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Se houver falhas no aplicativo durante uma chamada a uma DLL do sistema ou o código de outra pessoa, você precisará descobrir qual DLL estava ativa quando a falha ocorreu. Se você tiver uma falha em uma DLL fora do seu próprio programa, você pode identificar o local usando o **módulos** janela.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para descobrir onde ocorreu uma falha usando a janela Módulos  
  
1.  Observe o endereço onde a falha ocorreu.  
  
2.  Sobre o **depurar** menu, escolha **Windows**e clique em **módulos**.  
  
3.  No **módulos** janela, localize a **endereço** coluna. Você poderá precisar usar a barra de rolagem para vê-la.  
  
4.  Clique o **endereço** botão na parte superior da coluna para classificar as DLLs por endereço.  
  
5.  Examine a lista classificada para localizar a DLL cujo intervalo de endereço contém o local da falha.  
  
6.  Examine o **nome** e **caminho** colunas para ver o nome da DLL e o caminho.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando projetos de DLL](../debugger/debugging-dll-projects.md)   
 [Como usar a janela Módulos](../debugger/how-to-use-the-modules-window.md)