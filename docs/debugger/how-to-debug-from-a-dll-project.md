---
title: 'Como: depurar a partir de um projeto de DLL | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63581cee8816e72492a67a0981a9077b9fec2935
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>Como: depurar a partir de um projeto de DLL no Visual Studio
Uma maneira para depurar um projeto de DLL é para especificar o aplicativo de chamada nas propriedades do projeto do projeto de DLL e, em seguida, você pode iniciar a depuração do projeto de DLL em si. Para este método funcione, o aplicativo deve chamar a DLL, e a DLL deve estar no local onde o aplicativo espera encontrá-lo (caso contrário, o aplicativo pode localizar uma versão diferente da DLL e carregar que em vez disso, e não atingiu seus pontos de interrupção). Para outros métodos de depuração de DLLs, consulte [depurar projetos de DLL](../debugger/debugging-dll-projects.md).
  
Se uma DLL gerenciada é chamada pelo código nativo e você deseja depurar ambos, você pode especificar isso nas propriedades do projeto. Para obter mais informações, consulte [como: depurar no modo misto](../debugger/how-to-debug-in-mixed-mode.md).   

As páginas de propriedade C++ diferem no layout e o conteúdo do c# e Visual Basic páginas de propriedades. 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Para especificar o aplicativo de chamada em um projeto C++  
  
1.  Clique com botão direito no nó do projeto no **Solution Explorer** e selecione **propriedades**.  
  
2.  Verifique se o **configuração** campo na parte superior da janela é definido como **depurar**. 

    Um **depurar** configuração é necessária para este método. 
  
3.  Vá para **propriedades de configuração > depuração**.  
  
4.  No **depurador a iniciar** , escolha **depurador Local do Windows** ou **Remote Windows Debugger**.  
  
5.  No **comando** ou **comando remoto** caixa, adicione o nome de caminho totalmente qualificado do aplicativo de chamada (como um arquivo .exe).

    ![Janela de propriedades de depuração](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  Adicionar quaisquer argumentos de programa necessário para o **argumentos de comando** caixa.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Para especificar o aplicativo de chamada em um projeto C# ou Visual Basic  
  
1.  Clique com botão direito no nó do projeto no **Solution Explorer** e selecione **propriedades**e, em seguida, selecione o **depurar** guia.

2.  Verifique se o **configuração** campo na parte superior da janela é definido como **depurar**.

3.  (.NET framework) Selecione **Iniciar programa externo**e adicione o nome de caminho totalmente qualificado do aplicativo de chamada.

4.  (.NET core) Selecione **executável** do **iniciar** lista e, em seguida, adicione o nome de caminho totalmente qualificado do aplicativo de chamada no **executável** campo. 
  
     Se você precisar adicionar argumentos de linha de comando do programa externo, adicioná-las a **argumentos de linha de comando** (ou **argumentos de aplicativo**) campo.

    ![Janela de propriedades de depuração](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  Se for necessário, você também pode chamar um aplicativo como uma URL. (Você poderá fazer isso se estiver depurando uma DLL gerenciada usada por um aplicativo local do ASP.NET.)  
  
     Em **iniciar ação**, selecione o **Iniciar navegador com URL:** botão de opção e preencha a URL.
  
### <a name="to-start-debugging-from-the-dll-project"></a>Para iniciar a depuração do projeto da DLL  
  
1.  Definir pontos de interrupção no projeto de DLL. 

2.  Clique com botão direito do projeto de DLL e escolha **definir como projeto de inicialização**. 

    (Além disso, certifique-se de que o **soluções configuração** campo ainda está definido como **depurar**.)   
  
3.  Iniciar a depuração (pressione F5, clique na seta verde ou clique **Depurar > Iniciar depuração**).

    Você atingirá os pontos de interrupção na DLL. Se você não conseguir atingir os pontos de interrupção, certifique-se de que a DLL de saída (por padrão, o **project\Debug** pasta) está em um local que o aplicativo de chamada espera encontrá-lo.
  
## <a name="see-also"></a>Consulte também  
 [Depurando projetos de DLL](../debugger/debugging-dll-projects.md)   
 [Configurações do projeto para configurações de depuração de C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configurações do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Configurações do projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)