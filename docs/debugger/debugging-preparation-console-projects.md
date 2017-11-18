---
title: "Preparação da depuração: Projetos de Console | Microsoft Docs"
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
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c4b5021db951acc6ed8ed750542febab9fdfbf4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-preparation-console-projects"></a>Preparação de depuração: projetos de console
Preparar para depurar um projeto de console é semelhante à preparar para depurar um projeto do Windows, com algumas considerações adicionais. Para obter mais informações, consulte [aplicativos dos Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), e [preparação de depuração: aplicativos de formulários do Windows (.NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Devido à semelhança de todos os aplicativos do console, este tópico abrange os seguintes tipos de projeto:  
  
-   Aplicativo do Console C#  
  
-   Aplicativo do Console do Visual Basic  
  
-   Aplicativo do Console C++ (.NET)  
  
-   Aplicativo do Console C++ (Win32)  
  
 Talvez seja preciso especificar argumentos de linha de comando para o aplicativo de console. Para obter mais informações, consulte [configurações de projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [configurações de projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), ou [configurações do projeto para configurações de depuração do c# ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
 Como todas as propriedades do projeto, esses argumentos persistem entre sessões de depuração e entre sessões do Visual Studio. Portanto, se o aplicativo de console é aquele que você tem depurado anteriormente, lembre-se de que haja argumentos de sessões anteriores inseridos no  **\<projeto > páginas de propriedade** caixa de diálogo.  
  
 Um aplicativo de console usa o **Console** janela para aceitar a entrada e para exibir mensagens de saída. Para gravar o **Console** janela, o aplicativo deve usar o **Console** objeto em vez do objeto de depuração. Para gravar o **saída do Visual Studio** janela, use o objeto de depuração, como de costume. Confira se você sabe onde seu aplicativo está sendo gravado ou você pode procurar mensagens no local errado. Para obter mais informações, consulte [classe Console](/dotnet/api/system.console), [classe Debug](/dotnet/api/system.diagnostics.debug), e [a janela de saída](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Iniciando o aplicativo  
 Quando alguns aplicativos do console iniciarem, eles são executados até a conclusão e, em seguida, são fechados. Esse comportamento pode não oferecer tempo suficiente para interromper a execução e a depuração. Para poder depurar um aplicativo, use um dos seguintes procedimentos para iniciar o aplicativo:  
  
-   O aplicativo inicia a execução e é executado até atingir o ponto de interrupção.  
  
-   Seus aplicativo inicia e é interrompido imediatamente na primeira linha do código-fonte.  
  
-   Em uma janela de código de origem, clique em uma linha e selecione **executar até o cursor**.  
  
     Seu aplicativo é iniciado e executado até a linha selecionada, ou até um ponto de interrupção, se o ponto de interrupção for atingido antes da linha.  
  
 Quando você depura um aplicativo de console, inicie o aplicativo do prompt de comando em vez do Visual Studio. Nesse caso, você poderá iniciar o aplicativo de prompt de comando e anexar o depurador do Visual Studio a ele. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Quando você iniciar um aplicativo de console do Visual Studio, o **Console** janela às vezes aparece por trás da janela do Visual Studio. Se você tentar iniciar o aplicativo de console do Visual Studio e nada acontecer, tente mover a janela do Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código nativo](../debugger/debugging-native-code.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Tipos de projeto do Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipos de projeto do C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configurações de projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Segurança do depurador](../debugger/debugger-security.md)