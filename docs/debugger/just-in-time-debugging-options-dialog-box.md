---
title: "Caixa de diálogo de opções Just-In-Time, depuração, | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4648ecb0ce1b62256cdf2fe297c0d8cb4ccb17e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Caixa de diálogo Just-In-Time, Depuração, Opções
Para acessar o **Just-In-Time** página, vá para o **ferramentas** menu e clique em **opções**. No **opções** caixa de diálogo caixa, expanda o **depuração** nó e selecione **Just-In-Time**. Essa página permite habilitar a depuração Just-In-Time para o código gerenciado, o código nativo e o script. Para obter mais informações, consulte [depuração Just-in-](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Você pode habilitar a depuração Just-In-Time para estes tipos de programa:  
  
-   Gerenciado  
  
-   Nativo  
  
-   script  
  
 A depuração Just-In-Time é uma técnica para depurar um programa que é iniciado fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você pode executar um programa criado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fora do ambiente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se você tiver habilitado a depuração Just-In-Time, uma falha exibirá uma caixa de diálogo que perguntará se você quer depurar.  
  
## <a name="associated-warnings"></a>Avisos associados  
 Quando você visita a esta página do **opções** caixa de diálogo, você poderá ver uma mensagem de aviso como esta:  
  
 **Outro depurador se registrou como Just-In-Time depurador. Para reparar, habilite Just-In-Time depurar ou executar o reparo do Visual Studio.**  
  
 Essa mensagem ocorrerá se você tiver outro depurador, possivelmente uma versão anterior do depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], definida como o depurador Just-In-Time.  
  
 Outra mensagem que você pode ver é o seguinte:  
  
 **Just-In-Time depuração detectados erros de registro. Para reparar, habilite Just-In-Time depurar ou executar o reparo do Visual Studio.**  
  
 Se você ver algum desses avisos, depuração com Just-In-Time [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] requer privilégios de administrador até que você resolveu o problema. Se você tentar habilitar como um não administrador nessas condições, verá a seguinte mensagem de erro:  
  
 **O acesso é negado. Um administrador habilitar Just-In-Time de depuração ou repare a instalação do Visual Studio.**  
  
## <a name="see-also"></a>Consulte também  
 [Depurando, caixa de diálogo Opções](../debugger/debugging-options-dialog-box.md)   
 [Como especificar configurações do depurador](../debugger/how-to-specify-debugger-settings.md)