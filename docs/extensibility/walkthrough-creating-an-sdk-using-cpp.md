---
title: 'Passo a passo: Criando um SDK usando C++ | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc30e3236f81f558f3794bb459f6da3edbdaa63d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Passo a passo: Criando um SDK usando C++
Este passo a passo mostra como criar uma nativo matemática biblioteca C++ SDK, o pacote SDK como um Visual Studio extensão (VSIX) e, em seguida, usá-lo para criar um aplicativo. Passo a passo é dividida nestas etapas:  
  
-   [Para criar o nativo e as bibliotecas de tempo de execução do Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Para criar o projeto de extensão NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Para criar um aplicativo de exemplo que usa a biblioteca de classe](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a>Para criar o nativo e as bibliotecas de tempo de execução do Windows  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Na lista de modelos, expanda **Visual C++**, **da Windows Store**e, em seguida, selecione o **DLL (aplicativos da Windows Store)** modelo. No **nome** , especifique `NativeMath`e, em seguida, escolha o **Okey** botão.  
  
3.  Atualize NativeMath.h para coincidir com o código a seguir.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Atualize NativeMath.cpp para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  Em **Solution Explorer**, abra o menu de atalho para **solução 'NativeMath'**e, em seguida, escolha **adicionar**, **novo projeto**.  
  
6.  Na lista de modelos, expanda **Visual C++**e, em seguida, selecione o **o componente de tempo de execução do Windows** modelo. No **nome** , especifique `NativeMathWRT`e, em seguida, escolha o **Okey** botão.  
  
7.  Atualize Class1. h para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Atualize Class1.cpp para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
##  <a name="createVSIX"></a>Para criar o projeto de extensão NativeMathVSIX  
  
1.  Em **Solution Explorer**, abra o menu de atalho para **solução 'NativeMath'**e, em seguida, escolha **adicionar**, **novo projeto**.  
  
2.  Na lista de modelos, expanda **Visual C#**, **extensibilidade**e, em seguida, selecione **pacote VSIX**. No **nome** , especifique **NativeMathVSIX**e, em seguida, escolha o **Okey** botão.  
  
3.  Quando o designer de manifesto do VSIX for exibida, feche-o.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para **source.extension.vsixmanifest**e, em seguida, escolha **Exibir código**.  
  
5.  Use o XML a seguir para substituir o XML existente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  Em **Solution Explorer**, abra o menu de atalho para o **NativeMathVSIX** do projeto e, em seguida, escolha **adicionar**, **Novo Item**.  
  
7.  Na lista de **itens do Visual C#**, expanda **dados**e, em seguida, selecione **arquivo XML**. No **nome** , especifique `SDKManifest.xml`e, em seguida, escolha o **Okey** botão.  
  
8.  Use esse XML para substituir o conteúdo do arquivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. Em **Solution Explorer**, no **NativeMathVSIX** de projeto, crie a estrutura de pastas:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. Em **Solution Explorer**, abra o menu de atalho para **solução 'NativeMath'**e, em seguida, escolha **Abrir pasta no Explorador de arquivos**.  
  
11. No **Explorador de arquivos**, copie \NativeMath\NativeMath.h e, em seguida, em **Gerenciador de soluções**, no **NativeMathVSIX** projeto, cole-o no \DesignTime\ Pasta CommonConfiguration\Neutral\Include\.  
  
     Copie \Debug\NativeMath\NativeMath.lib e, em seguida, cole-o na pasta \DesignTime\Debug\x86\.  
  
     Copie \Debug\NativeMath\NativeMath.dll e cole-o na pasta \Redist\Debug\x86\.  
  
     Copie DebugNativeMathWRTNativeMathWRT.dll e cole-o na pasta RedistDebugx86.  
  
     Copie DebugNativeMathWRTNativeMathWRT.winmd e cole-o na pasta ReferencesCommonConfigurationNeutral.  
  
     Copie DebugNativeMathWRTNativeMathWRT.pri e cole-o na pasta ReferencesCommonConfigurationNeutral.  
  
12. Na pasta \DesignTime\Debug\x86\, crie um arquivo de texto chamado NativeMathSDK.props e, em seguida, cole o seguinte conteúdo nele:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Na barra de menus, escolha **exibição**, **outras janelas**, **janela propriedades** (teclado: escolha a tecla F4).  
  
14. Em **Solution Explorer**, selecione o **NativeMathWRT.winmd** arquivo. No **propriedades** janela, altere o **ação de compilação** propriedade **conteúdo**e, em seguida, altere o **incluir VSIX** propriedade  **True**.  
  
     Repita esse processo para o **SimpleMath.pri** arquivo.  
  
     Repita esse processo para o **NativeMath.Lib** arquivo.  
  
     Repita esse processo para o **NativeMathSDK.props** arquivo.  
  
15. Em **Solution Explorer**, selecione o **NativeMath.h** arquivo. No **propriedades** janela, altere o **incluir VSIX** propriedade **True**.  
  
     Repita esse processo para o **NativeMath.dll** arquivo.  
  
     Repita esse processo para o **NativeMathWRT.dll** arquivo.  
  
     Repita esse processo para o **SDKManifest.xml** arquivo.  
  
16. Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
17. Em **Solution Explorer**, abra o menu de atalho para o **NativeMathVSIX** do projeto e, em seguida, escolha **Abrir pasta no Explorador de arquivos**.  
  
18. Em **Explorador de arquivos**, navegue até a pasta \bin\Debug\ e, em seguida, execute NativeMathVSIX.vsix para iniciar a instalação.  
  
19. Escolha o **instalar** botão, aguarde a conclusão da instalação e, em seguida, reinicie o Visual Studio.  
  
##  <a name="createSample"></a>Para criar um aplicativo de exemplo que usa a biblioteca de classe  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Na lista de modelos, expanda **Visual C++**, **da Windows Store**e, em seguida, selecione **aplicativo em branco**. No **nome** , especifique **NativeMathSDKSample**e, em seguida, escolha o **Okey** botão.  
  
3.  Em **Solution Explorer**, abra o menu de atalho para o **NativeMathSDKSample** do projeto e, em seguida, escolha **adicionar**, **referência**.  
  
4.  Sobre o **propriedades comuns**, **estrutura e referências** página de propriedades, na lista de tipos de referência, expanda **Windows**e, em seguida, selecione **extensões** . No painel de detalhes, selecione o **SDK de matemática nativo** extensão e, em seguida, escolha o **adicionar nova referência** botão.  
  
5.  No **adicionar referência** caixa de diálogo, selecione o **SDK de matemática nativo** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
6.  Exiba as propriedades do projeto para NativeMathSDKSample.  
  
     As propriedades que você definiu no NativeMathSDK.props foram aplicadas quando você adicionou a referência. Você pode verificar isso examinando o **diretórios VC + +** propriedade do projeto do **propriedades de configuração**.  
  
7.  Em **Solution Explorer**, abra MainPage. XAML e, em seguida, use o XAML a seguir para substituir seu conteúdo:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  Atualize Mainpage.xaml.h para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. Atualize MainPage.xaml.cpp para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. Pressione a tecla F5 para executar o aplicativo.  
  
11. No aplicativo, insira qualquer dois números, selecione uma operação e, em seguida, escolha o  **=**  botão.  
  
     O resultado correto é exibido.  
  
 Este passo a passo mostrou como criar e usar um SDK de extensão para chamar um [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca e não[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca.  
  
## <a name="next-steps"></a>Próximas etapas  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um SDK usando c# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Criar um Software Development Kit](../extensibility/creating-a-software-development-kit.md)