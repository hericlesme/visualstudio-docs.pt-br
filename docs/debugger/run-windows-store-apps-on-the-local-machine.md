---
title: Executar aplicativos UWP no computador local | Microsoft Docs
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
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08e0108a3fb7a93dc19fe1aa96988912068ace70
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>Executar aplicativos UWP no computador local
![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Para depurar, testar ou executar análise de desempenho em um aplicativo UWP, você pode executar o aplicativo no mesmo computador que hospeda o Visual Studio. Se a tela do dispositivo for habilitada para toque, você poderá ativar a funcionalidade completa do aplicativo; do contrário, você estará limitado aos gestos do mouse e do teclado.  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>Como executar em um computador local  
 Para executar o aplicativo no computador local, selecione **Máquina Local** na lista suspensa ao lado do botão Iniciar depuração, o depurador **padrão** barra de ferramentas.  
  
 ![Executar na máquina Local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 Se você não conseguir ver o **padrão** barra de ferramentas, clique no **exibição** , aponte para **barras de ferramentas**e, em seguida, clique em **padrão**.  
  
 A escolha que você faz na lista suspensa persiste no arquivo de propriedades do projeto e se torna o destino de execução padrão.  
  
 Você também pode definir o destino de execução diretamente no arquivo de propriedades do projeto. Clique no nome do projeto em **Solution Explorer** e, em seguida, escolha **propriedades**. Siga um destes procedimentos:  
  
-   Em projetos c# e Visual Basic, clique em **depurar** e, em seguida, selecione **Máquina Local** do **dispositivo de destino** lista suspensa.  
  
     ![C &#35; e a página de propriedades de projeto do Visual Basic](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   Em projetos C++ e JavaScript, expanda o **propriedades de configuração** nó, clique em **depuração**e, em seguida, selecione **depurador Local** do **depurador para iniciar** lista.  
  
     ![C &#43; &#43; página de propriedades de projeto de JavaScript e](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  