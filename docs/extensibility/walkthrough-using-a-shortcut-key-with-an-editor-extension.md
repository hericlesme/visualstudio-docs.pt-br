---
title: "Passo a passo: Usando uma tecla de atalho com uma extensão de Editor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8066ac52076afd9c0f8cb697ca51327188c9c216
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Passo a passo: Usando uma tecla de atalho com uma extensão de Editor
Você pode responder a teclas de atalho em sua extensão de editor. A instrução a seguir mostra como adicionar um adorno de exibição para uma exibição de texto usando uma tecla de atalho. Este passo a passo é baseada no modelo de editor de adorno de visor, e permite que você adicione o adorno usando o caractere +.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto do Managed Extensibility Framework (MEF)  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual C# / extensibilidade**, em seguida, **projeto VSIX**.) Nome da solução `KeyBindingTest`.  
  
2.  Adicione um modelo de item de adorno de texto do Editor para o projeto e denomine- `KeyBindingTest`. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Adicione as seguintes referências e defina **CopyLocal** para `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 No arquivo de classe KeyBindingTest, altere o nome de classe para PurpleCornerBox. Use lâmpada que aparece na margem esquerda para fazer outras alterações apropriadas. Dentro do construtor, altere o nome da camada de adorno de **KeyBindingTest** para **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Definindo o filtro de comando  
 O filtro de comando é uma implementação de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, que trata o comando instanciando o adorno.  
  
1.  Adicione um arquivo de classe e denomine- `KeyBindingCommandFilter`.  
  
2.  Adicione o seguinte usando instruções.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  A classe denominada KeyBindingCommandFilter deve herdar de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Adicione campos privados para o modo de texto, o comando seguinte na cadeia de comando e um sinalizador para representar se o filtro de comando já foi adicionado.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Adicione um construtor que define o modo de texto.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementar o `QueryStatus()` método da seguinte maneira.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementar o `Exec()` método para que ele adiciona uma caixa roxa para o modo de exibição se um + caractere é digitado.  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter"></a>Adicionar o filtro de comando  
 O provedor de adorno deve adicionar um filtro de comando para a exibição de texto. Neste exemplo, o provedor implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para escutar eventos de criação de exibição de texto. Este provedor de adorno também exporta a camada de adorno, que define a ordem Z do adorno.  
  
1.  No arquivo KeyBindingTestTextViewCreationListener, adicione o seguinte usando instruções:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  Na definição de camada de adorno, alterar o nome de AdornmentLayer de **KeyBindingTest** para **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Para obter o adaptador de exibição de texto, você deve importar o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Alterar o <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que ele adiciona o `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  O `AddCommandFilter` manipulador obtém o adaptador de exibição de texto e adiciona o filtro de comando.  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## <a name="making-the-adornment-appear-on-every-line"></a>Tornando o adorno aparecem em cada linha  
 O adorno original é exibido em cada caractere 'a' em um arquivo de texto. Agora que alteramos o código para adicionar o adorno em resposta ao caractere '+', ele adiciona o adorno somente na linha em que a '+' é digitado. Podemos alterar o código de adornos para que o adorno mais uma vez é exibido em cada 'a'.  
  
 No arquivo KeyBindingTest.cs, altere o método CreateVisuals() para iterar por todas as linhas no modo de exibição para decorar o caractere 'a'.  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
  
1.  Compile a solução KeyBindingTest e executá-lo na instância experimental.  
  
2.  Criar ou abrir um arquivo de texto. Algumas palavras que contém o caractere de tipo 'a' e, em seguida, digite + em qualquer lugar no modo de exibição de texto.  
  
     Um quadrado roxo deve aparecer em cada caractere 'a' no arquivo.