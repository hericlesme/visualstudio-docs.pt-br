---
title: 'Como: Localizar em qual DLL o programa falhado | Microsoft Docs'
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
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8dc06d433739b4c0706374a691474207a45c5766
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464894"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Como localizar em qual DLL o programa falhou
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: localizar qual DLL o programa falhou em](https://docs.microsoft.com/visualstudio/debugger/how-to-find-which-dll-your-program-crashed-in).  
  
OBSERVAÇÃO]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se houver falhas no aplicativo durante uma chamada a uma DLL do sistema ou o código de outra pessoa, você precisará descobrir qual DLL estava ativa quando a falha ocorreu. Se você tiver uma falha em uma DLL fora do seu próprio programa, você pode identificar o local usando o **módulos** janela.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para descobrir onde ocorreu uma falha usando a janela Módulos  
  
1.  Observe o endereço onde a falha ocorreu.  
  
2.  Sobre o **Debug** menu, escolha **Windows**e clique em **módulos**.  
  
3.  No **módulos** janela, localizar o **endereço** coluna. Você poderá precisar usar a barra de rolagem para vê-la.  
  
4.  Clique o **endereço** botão na parte superior da coluna para classificar as DLLs por endereço.  
  
5.  Examine a lista classificada para localizar a DLL cujo intervalo de endereço contém o local da falha.  
  
6.  Examine os **nome** e **caminho** colunas para ver o nome da DLL e o caminho.  
  
## <a name="see-also"></a>Consulte também  
 [Como: depurar DLLs nativas](../debugger/how-to-debug-native-dlls.md)   
 [Como usar a janela Módulos](../debugger/how-to-use-the-modules-window.md)





