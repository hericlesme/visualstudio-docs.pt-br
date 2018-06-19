---
title: 'Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cca12f7c04b51bcf2b695e00d9305a7feb72ebc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144889"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo
Você pode definir seu próprio tipo de conteúdo e vincular uma extensão de nome de arquivo usando as extensões do editor Managed Extensibility Framework (MEF). Em alguns casos, a extensão de nome de arquivo já foi definida por um serviço de linguagem; No entanto, para usá-lo com MEF você ainda deve vinculá-lo para um tipo de conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual C# / extensibilidade**, em seguida, **projeto VSIX**.) Nome da solução `ContentTypeTest`.  
  
2.  No **source.extension.vsixmanifest** arquivo, vá para o **ativos** guia e defina o **tipo** campo **Microsoft.VisualStudio.MefComponent**, o **fonte** campo **um projeto na solução atual**e o **projeto** campo para o nome do projeto.  
  
## <a name="defining-the-content-type"></a>Definindo o tipo de conteúdo  
  
1.  Adicione um arquivo de classe e denomine- `FileAndContentTypes`.  
  
2.  Adicione referências aos assemblies a seguir:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Adicione o seguinte `using` diretivas.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Declare uma classe estática que contém as definições.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  Nessa classe, exportar um <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> denominado "hid" e declarar sua definição base deve ser "texto".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Vinculando uma extensão de nome de arquivo para um tipo de conteúdo  
  
-   Para mapear esse tipo de conteúdo para uma extensão de nome de arquivo, exportar um <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que tem a extensão ". HID" e o tipo de conteúdo "hid".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Adicionando o tipo de conteúdo para uma exportação de Editor  
  
1.  Crie uma extensão de editor. Por exemplo, você pode usar a extensão de glifo de margem descrita em [passo a passo: Criando um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Adicione a classe definida nesse procedimento.  
  
3.  Quando você exporta a classe de extensão, adicione um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> do tipo "hid" a ele.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)