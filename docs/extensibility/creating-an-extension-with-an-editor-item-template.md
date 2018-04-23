---
title: Criando uma extensão com um modelo de Item Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60f10479e0ce6fa08e888d92556ff47b5d82af66
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Criando uma extensão com um modelo de Item Editor
Você pode usar modelos de item que são incluídos no SDK do Visual Studio para criar extensões de editor básico que adiciona classificadores, ornamentos e as margens no Editor. Os modelos de item editor estão disponíveis para projetos do Visual c# ou Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Criando uma extensão de classificação  
 O modelo de item de classificação de Editor cria um classificador de editor que o texto apropriado de cores (neste caso, tudo) em qualquer arquivo de texto.  
  
1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic** e, em seguida, clique em **extensibilidade**. No **modelos** painel, selecione **projeto VSIX**. Na caixa **Nome**, digite `TestClassifier`. Clique em **OK**.  
  
2.  No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. Vá para o Visual c# **extensibilidade** nó e selecione **Editor classificador**. Deixe o nome de arquivo padrão (EditorClassifier1.cs).  
  
3.  Há três arquivos de código, da seguinte maneira:  
  
    -   EditorClassifier1.cs contém o `EditorClassifier1` classe.  
  
    -   EditorClassifier1ClassificationDefinition.cs contém o `OEditorClassifier1ClassificationDefinition` classe.  
  
    -   EditorClassifier1Format.cs contém o `EditorClassifier1Format` classe.  
  
    -   EditorClassifier1Provider.cs contém o `EditorClassifier1Provider` classe.  
  
4.  Compile o projeto e comece a depuração. É exibida a instância experimental do Visual Studio.  
  
     Se você abrir um arquivo de texto, todo o texto é sublinhado em um plano de fundo violeta.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Criando uma extensão de adorno relativos a texto  
 O modelo de adorno de texto do Editor cria um adorno relativos a texto que decora todas as ocorrências do caractere de texto 'a' usando uma caixa com um contorno vermelho e um plano de fundo azul. Ele é relativo ao texto porque a caixa sempre sobreposições 'a' caracteres, mesmo quando eles são movidos ou reformatados.  
  
1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic** e, em seguida, clique em **extensibilidade**. No **modelos** painel, selecione **projeto VSIX**. Na caixa **Nome**, digite `TestAdornment`. Clique em **OK**.  
  
2.  No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. Vá para o Visual c# **extensibilidade** nó e selecione **adorno do Editor de texto**. Deixe o nome de arquivo padrão (TextAdornment1.cs/vb).  
  
3.  Há dois arquivos de código, da seguinte maneira:  
  
    -   TextAdornment1.cs contém o `TextAdornment1` classe.  
  
    -   extAdornment1TextViewCreationListener.cs contém o `TextAdornment1TextViewCreationListener` classe.  
  
4.  Compile o projeto e comece a depuração. A instância experimental aparece. Se você abrir um arquivo de texto, todos os 'a' caracteres de texto são realçados em vermelho em um plano de fundo azul.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Criando uma extensão de adorno relativo ao visor  
 O modelo de adorno de visor do Editor cria um adorno de visor relativo que adiciona uma caixa violeta que tem um contorno vermelho ao canto superior direito do visor.  
  
> [!NOTE]
>  O *visor* é a área de exibição de texto que está sendo exibida.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Para criar uma extensão de adorno visor usando o modelo de adorno de visor do Editor  
  
1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic** e, em seguida, clique em **extensibilidade**. No **modelos** painel, selecione **projeto VSIX**. Na caixa **Nome**, digite `ViewportAdornment`. Clique em **OK**.  
  
2.  No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. Vá para o Visual c# **extensibilidade** nó e selecione **Editor visor adorno**. Deixe o nome de arquivo padrão (ViewportAdornment1.cs/vb).  
  
3.  Há dois arquivos de código, da seguinte maneira:  
  
    -   ViewportAdornment1.cs contém o `ViewportAdornment1` classe.  
  
    -   ViewportAdornment1TextViewCreationListener.cs contém o `ViewportAdornment1TextViewCreationListener` classe  
  
4.  Compile o projeto e comece a depuração. A instância experimental aparece. Se você criar um novo arquivo de texto, uma caixa violeta que tem um contorno vermelho é exibida no canto superior direito do visor.  
  
## <a name="creating-a-margin-extension"></a>Criando uma extensão de margem  
 O modelo de margem de Editor cria uma margem de verde é exibida junto com as palavras "Hello world!" abaixo da barra de rolagem horizontal.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Para criar uma extensão da margem usando o modelo de margem do Editor  
  
1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic** e, em seguida, clique em **extensibilidade**. No **modelos** painel, selecione **projeto VSIX**. Na caixa **Nome**, digite `MarginExtension`. Clique em **OK**.  
  
2.  No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. Vá para o Visual c# **extensibilidade** nó e selecione **Editor visor adorno**. Deixe o nome de arquivo padrão (EditorMargin1.cs/vb).  
  
3.  Há dois arquivos de código, da seguinte maneira:  
  
    -   EditorMargin1.cs contém o `EditorMargin1` classe.  
  
    -   EditorMargin1Factory.cs contém o `EditorMargin1Factory` classe.  
  
4.  Compilar este projeto e iniciar a depuração. A instância experimental aparece. Se você abrir um arquivo de texto, uma margem verde com as palavras "Hello EditorMargin1" é exibida abaixo da barra de rolagem horizontal.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)