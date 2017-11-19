---
title: Depurando projetos DLL | Microsoft Docs
ms.custom: 
ms.date: 05/23/2017
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
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92d888c04827f3df2c9bc5ede33d4dfd9a6742dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-dll-projects-from-visual-studio"></a>Depurando projetos DLL do Visual Studio
Os seguintes modelos do Visual Studio criam DLLs:  
  
-   Biblioteca de Classes (C++, C# e Visual Basic)   

-   (C++): projeto de DLL do Console Win32
  
     Para obter mais informações, consulte [técnicas de depuração MFC](../debugger/mfc-debugging-techniques.md).

-   (C++, C# e Visual Basic): Biblioteca de Controle Windows Forms
  
     Depuração de uma biblioteca de controle de formulários do Windows é semelhante a depuração de um projeto de biblioteca de classe. Na maioria dos casos, você chamará o controle do Windows de outro projeto. Ao depurar o projeto de chamada, você poderá entrar no código do controle do Windows, definir pontos de interrupção e executar outras operações de depuração. Para obter mais informações, consulte [controles dos Windows Forms](/dotnet/framework/winforms/controls/index).  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Criação de uma versão de depuração  
 Não importa como você inicia a depuração, certifique-se de compilar a versão de Depuração da DLL primeiro e verifique se a versão de Depuração está no local onde o aplicativo espera encontrá-la. Isso pode parecer óbvio, mas se você esquecer desta etapa, o aplicativo poderá encontrar uma versão diferente da DLL e carregá-la. O programa continuará a ser executado enquanto você se pergunta o porquê do ponto de interrupção nunca ter sido atingido. Quando você estiver depurando, você pode verificar quais DLLs seu programa carregou abrindo o depurador **módulos** janela. O **módulos** janela lista cada DLL ou EXE carregados no processo que você está depurando. Para obter mais informações, consulte [como: usar a janela módulos](../debugger/how-to-use-the-modules-window.md).  
 Para que o depurador conecte-se ao código escrito em C++, o código deverá emitir `DebuggableAttribute`. Você pode adicionar isso ao seu código automaticamente por meio da vinculação com a [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) opção de vinculador.  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Depuração de modo misto  
 O aplicativo de chamada que chama a DLL pode ser escrito em código gerenciado ou em código nativo. Se a DLL gerenciada for chamada por código nativo e você quiser depurar os dois, os depuradores gerenciados e nativos deverão estar habilitados. Você pode selecionar isso no  **\<projeto > páginas de propriedade** caixa de diálogo ou janela. Como você faz isso depende de a depuração ser iniciada do projeto de DLL ou do projeto de aplicativo de chamada. Para obter mais informações, consulte [como: depurar no modo misto](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Alterar as configurações padrão  
 Quando você cria um projeto de aplicativo de console com o modelo de projeto, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para as configurações de Depuração e Versão. Se necessário, você pode alterar essas configurações. Para obter mais informações, consulte [configurações de projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [configurações do projeto para configurações de depuração do c#](../debugger/project-settings-for-csharp-debug-configurations.md), [as configurações de projeto para depurar a configuração no Visual Basic ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), e [como: definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Maneiras de depurar a DLL  
 Cada um dos projetos nesta seção cria uma DLL. Você não pode executar uma DLL diretamente. Ela deve ser chamada por um aplicativo, geralmente um EXE. Para obter mais informações, consulte [criando e gerenciando projetos do Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects). O aplicativo de chamada pode conter qualquer um dos seguintes critérios:  
  
-   Um aplicativo compilado em outro projeto na mesma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contém a biblioteca de classes.  
  
-   Um aplicativo existente já implantado em um teste ou em um computador de produção.  
  
-   Localizado na Web e acessado por meio de uma URL.  
  
-   Um aplicativo da Web que contém uma página da Web que insere a DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Depurando o aplicativo de chamada  
Para depurar uma DLL, comece depurando o aplicativo de chamada, normalmente um EXE ou um aplicativo Web. Há várias maneiras de depurá-lo.  
  
-   Se você tiver um projeto para o aplicativo de chamada, você pode abrir o projeto e iniciar a execução do **depurar** menu. Para obter mais informações, consulte [guia de Introdução com o depurador](../debugger/getting-started-with-the-debugger.md).  
  
-   Se o aplicativo de chamada for um programa existente já implantado em um teste ou em um computador de produção e já estiver em execução, você poderá conectar-se a ele. Use este método se a DLL for um controle hospedado pelo Internet Explorer ou um controle em uma página da Web. Para obter mais informações, consulte [como: anexar a um processo em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
-   Você pode depurá-lo no projeto da DLL. Para obter mais informações, consulte [como: depuração de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   Você poderá depurá-lo do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [janela imediata](#vxtskdebuggingdllprojectstheimmediatewindow). Nesse caso, o **imediato** janela desempenha a função de aplicativo.  
  
Antes de começar a depurar o aplicativo de chamada, convém definir um ponto de interrupção na biblioteca de classes. Para obter mais informações, consulte [usando pontos de interrupção](../debugger/using-breakpoints.md). Quando o ponto de interrupção for atingido, você poderá percorrer o código, observando a ação em cada linha até isolar o problema. Para obter mais informações, consulte [navegar pelo código no depurador](../debugger/navigating-through-code-with-the-debugger.md).
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Janela imediata  
 Você pode avaliar funções ou métodos na DLL sem ter um aplicativo de chamada. Faça a depuração no tempo de design e você usar o **imediato** janela. Para depurar dessa maneira, execute as seguintes etapas enquanto o projeto da DLL estiver aberto:  
  
1.  Abra o depurador **imediato** janela.  
  
2.  Para testar um método chamado `Test` na classe `Class1`, crie uma instância de um objeto do tipo `Class1` digitando o seguinte código em C# na janela Imediato. Esse código gerenciado funciona para o Visual Basic e C++, com as alterações de sintaxe apropriadas:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     No C#, todos os nomes devem ser totalmente qualificados. Além disso, todos os métodos ou variáveis devem estar no escopo e no contexto atuais da sessão de depuração.  
  
3.  Supondo que `Test` usa uma `int` parâmetro, avaliar `Test` usando o **imediato** janela:  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     O resultado será impressa no **imediato** janela.  
  
4.  Você pode continuar a depuração do `Test` colocando um ponto de interrupção dentro dele e avaliando a função novamente:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     O ponto de interrupção será atingido e você poderá depurar `Test`. Após a execução do `Test`, o Depurador voltará ao modo Design.

## <a name="vxtskdebuggingdllprojectsexternal"></a>Depurar uma DLL externa de um projeto de C++

Se você estiver depurando um DLL externo ao seu projeto, os recursos de depuração disponíveis (como percorrendo o código) dependem de [configuração de depuração da DLL](#vxtskdebuggingdllprojectsbuildingadebugversion) quando ele foi criado e se o [arquivo. PDB](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e outros arquivos necessários para a DLL estão disponíveis.

O projeto precisa ser capaz de encontrar a DLL e o arquivo. PDB usado para depuração. Você pode criar uma tarefa de compilação personalizada para copiar esses arquivos para o  **\<pasta do projeto > \Debug.** pasta de saída, ou você pode copiar os arquivos para a pasta de saída manualmente.

Você pode definir facilmente os locais dos arquivos de cabeçalho e *.lib nas páginas de propriedade (clique com botão direito do C++ e escolha **exibir propriedades**e, em seguida, escolha **todas as configurações de**) sem a necessidade de copiar -los em sua pasta de saída:

- Pasta de C/C++ (categoria geral) - Especifique a pasta que contém arquivos de cabeçalho no **diretórios de inclusão adicionais** campo.
- Pasta de vinculador (categoria geral) - Especifique a pasta que contém o arquivo. lib no **diretórios de bibliotecas adicionais** campo. 
- Pasta de vinculador (categoria de entrada) - Especifique o caminho completo e nome de arquivo para o arquivo. lib no **dependências adicionais** campo.

Quando a configuração estiver correta, você pode depurar iniciando a execução a partir de **depurar** menu.

Para obter mais informações sobre configurações de projeto, consulte [páginas de propriedade (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Tipos de projeto do Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipos de projeto do C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configurações de projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configurações do projeto para configurações de depuração de C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configurações do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Segurança do depurador](../debugger/debugger-security.md)