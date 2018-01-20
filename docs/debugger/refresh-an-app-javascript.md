---
title: Atualizar um aplicativo UWP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
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
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: ef42c0208b973707294a842376ef737216e13774
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Atualizar um aplicativo UWP no Visual Studio
  
 Você pode fazer alterações ao seu código enquanto está depurando e depois atualizar um aplicativo UWP usando JavaScript escolhendo o **atualizar aplicativo do Windows** botão o **depurar** barra de ferramentas. Dessa forma, o aplicativo é recarregado sem parar e reiniciar o depurador. A funcionalidade Atualizar permite que você modifique o código HTML, CSS e JavaScript e veja rapidamente o resultado. Esse recurso tem suporte para aplicativos UWP.  
  
 A atualização não mantém o estado do aplicativo nem reflete as seguintes alterações feitas no aplicativo:  
  
-   Alterações no arquivo de manifesto do pacote, inclusive nas imagens especificadas no manifesto do pacote.  
  
-   Alterações em referências, como a adição ou a remoção de uma referência de SDK, ou alterações nos componentes do Windows Runtime  (arquivos .winmd).  
  
-   Alterações em recursos, como as efetuadas nas cadeias de caracteres dos arquivos .resjson.  
  
-   Alterações em arquivos de projeto que resultam em mudanças de nome de caminho, novos arquivos de projeto ou arquivos excluídos.  
  
-   Alterações em propriedades de projetos e de itens, como as feitas no dispositivo de depuração selecionado, ou alterações na ação de pacote para um arquivo (na janela Propriedades).  
  
> [!IMPORTANT]
>  Ao alterar referências, alterar o manifesto do pacote ou fazer outras alterações especificadas na lista anterior, você precisa interromper e reiniciar o depurador para atualizar os arquivos de origem HTML, CSS e JavaScript.  
  
### <a name="to-refresh-an-app"></a>Para atualizar um aplicativo  
  
1.  Com o seu projeto UWP aberto no Visual Studio, selecione **Máquina Local** como o destino de depuração.
  
     ![Lista de destino de depuração selecione](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Pressione F5 para executar o aplicativo no modo de depuração.  
  
4.  Alterne para o Visual Studio. 
  
5.  Na home page do aplicativo UWP, edite algumas do HTML.
  
7.  Clique o **atualizar aplicativo do Windows** botão, que tem esta aparência: ![botão do aplicativo de atualização do Windows](../debugger/media/js_refresh.png "JS_Refresh"). (Ou pressione F4.)  
  
8.  Altere para o aplicativo. O aplicativo é recarregado e atualizado HTML usado para renderizar o aplicativo.
  
## <a name="see-also"></a>Consulte também  
 [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)