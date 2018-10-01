---
title: Atualizar um aplicativo (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca647572eac68dcf70d21b7ed687212a0229568f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464312"
---
# <a name="refresh-an-app-javascript"></a>Atualizar um aplicativo (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [atualizar um aplicativo (JavaScript)](https://docs.microsoft.com/visualstudio/debugger/refresh-an-app-javascript).  
  
Aplica-se ao Windows e Windows Phone] (... /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Você pode fazer alterações ao seu código enquanto você está depurando e, em seguida, atualizar um aplicativo da Store usando JavaScript escolhendo o **atualizar o Windows app** botão a **depurar** barra de ferramentas. Dessa forma, o aplicativo é recarregado sem parar e reiniciar o depurador. A funcionalidade Atualizar permite que você modifique o código HTML, CSS e JavaScript e veja rapidamente o resultado. Esta funcionalidade tem suporte para os dois aplicativos da Windows Store e da Windows Phone Store.  
  
 A atualização não mantém o estado do aplicativo nem reflete as seguintes alterações feitas no aplicativo:  
  
-   Alterações no arquivo de manifesto do pacote, inclusive nas imagens especificadas no manifesto do pacote.  
  
-   Alterações em referências, como a adição ou a remoção de uma referência de SDK, ou alterações nos componentes do Windows Runtime  (arquivos .winmd).  
  
-   Alterações em recursos, como as efetuadas nas cadeias de caracteres dos arquivos .resjson.  
  
-   Alterações em arquivos de projeto que resultam em mudanças de nome de caminho, novos arquivos de projeto ou arquivos excluídos.  
  
-   Alterações em propriedades de projetos e de itens, como as feitas no dispositivo de depuração selecionado, ou alterações na ação de pacote para um arquivo (na janela Propriedades).  
  
> [!IMPORTANT]
>  Ao alterar referências, alterar o manifesto do pacote ou fazer outras alterações especificadas na lista anterior, você precisa interromper e reiniciar o depurador para atualizar os arquivos de origem HTML, CSS e JavaScript.  
  
### <a name="to-refresh-an-app"></a>Para atualizar um aplicativo  
  
1.  No Visual Studio, crie um novo projeto usando o modelo de projeto do Aplicativo de Navegação.  
  
     Este pode ser um aplicativo da Windows Store, da Windows Phone Store ou um aplicativo universal.  
  
2.  Com o modelo aberto no Visual Studio, escolha um destino de depuração.  
  
     Se um projeto do Windows Phone for seu projeto de inicialização atual, selecione o emulador do Windows Phone para o destino de depuração. Caso contrário, selecione **simulador** ou **Máquina Local**.  
  
     ![Lista de destino de depuração Select](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3.  Pressione F5 para executar o aplicativo no modo de depuração.  
  
4.  Alterne para o Visual Studio. (Pressione F12.)  
  
5.  Na **Gerenciador de soluções**, no **páginas** > **doméstica** pasta, abra home. HTML.  
  
6.  Altere o texto do título da página, de  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     para outra coisa, por exemplo:  
  
    ```html  
    Hello!  
    ```  
  
7.  Clique o **atualizar o Windows app** botão, que se parece com isso: ![botão de aplicativo do Windows de atualização](../debugger/media/js-refresh.png "JS_Refresh"). (Ou pressione F4.)  
  
8.  Altere para o aplicativo. O aplicativo é recarregado sem que o depurador seja reiniciado, e o novo título da página é exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)



