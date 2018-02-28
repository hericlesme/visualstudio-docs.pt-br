---
title: "Adaptando um código herdado para o Editor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ef1bce81e20772660a6074c15bd5dad494804373
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="adapting-legacy-code-to-the-editor"></a>Adaptando um código herdado para o Editor
O editor do Visual Studio tem muitos recursos que você pode acessar de componentes de código existentes. As instruções a seguir mostram como adaptar um componente não MEF, por exemplo, um VSPackage consumir a funcionalidade do editor. As instruções também mostram como usar adaptadores para obter os serviços do editor no código gerenciado e não gerenciado.  
  
## <a name="editor-adapters"></a>Adaptadores de editor  
 Adaptadores de editor ou correções, são wrappers de objetos de editor que também expõe as classes e interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop> API. Você pode usar os adaptadores de mover entre serviços do editor de não por exemplo, os comandos de shell do Visual Studio e serviços do editor. (Isso é como o editor está hospedado no momento no Visual Studio.) Adaptadores também habilitar herdados editor e linguagem de extensões de serviços funcionar corretamente no Visual Studio.  
  
## <a name="using-editor-adapters"></a>Usando adaptadores de Editor  
 O <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> fornece métodos que alterne entre as novas interfaces de editor e as interfaces herdadas e também métodos que criar adaptadores.  
  
 Se você estiver usando esse serviço em uma parte do componente MEF, você pode importar o serviço da seguinte maneira.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Se você quiser usar esse serviço em um componente não MEF, siga as instruções na seção "Usando o Editor serviços em uma não-MEF componente do Visual Studio" neste tópico.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Alternar entre a nova API de Editor e a API herdado  
 Use os seguintes métodos para alternar entre um objeto editor e uma interface herdada.  
  
|Método|Conversão|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Converte um <xref:Microsoft.VisualStudio.Text.ITextBuffer> em um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Converte um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> em um <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Converte um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> em um <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Converte um <xref:Microsoft.VisualStudio.Text.Editor.ITextView> em um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Converte um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> em um <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Criando adaptadores  
 Use os seguintes métodos para criar adaptadores para interfaces herdadas.  
  
|Método|Conversão|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para um <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para um <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Criando adaptadores em código não gerenciado  
 Todas as classes de adaptador estão registradas para ser local co instanciável e pode ser instanciado usando o `VsLocalCreateInstance()` função.  
  
 Todos os adaptadores são criados usando os GUIDs que são definidos no arquivo de vsshlids.h em de... Pasta de \VisualStudioIntegration\Common\Inc\ da instalação do SDK do Visual Studio. Para criar uma instância de VsTextBufferAdapter, use o código a seguir.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Criando adaptadores em código gerenciado  
 No código gerenciado, você pode criar conjuntamente os adaptadores da mesma forma descrita para código não gerenciado. Você também pode usar um serviço MEF que permite que você crie e interaja com os adaptadores. Essa maneira de obter um adaptador permite um controle mais refinado do que quando criar conjuntamente.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Para criar um adaptador para IVsTextView  
  
1.  Adicione uma referência a Microsoft.VisualStudio.Editor.dll. Verifique se `CopyLocal` é definido como `false`.  
  
2.  Criar uma instância de <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, da seguinte maneira.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Chame o método `CreateX()`.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Usando o Editor do Visual Studio diretamente no código não gerenciado  
 O namespace Microsoft.VisualStudio.Platform.VSEditor e o namespace Microsoft.VisualStudio.Platform.VSEditor.Interop expõem interfaces COM-callable como interfaces IVx *. Por exemplo, a interface Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer é a versão COM o <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface. Do `IVxTextBuffer`, obter acesso a instantâneos de buffer, modificar o buffer, escutar eventos de alteração de texto no buffer e criar pontos de controle e intervalos. As etapas a seguir mostram como acessar um `IVxTextBuffer` de um `IVsTextBuffer`.  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Para obter um IVxTextBuffer  
  
1.  As definições para as interfaces IVx * são no arquivo VSEditor.h em de... Pasta de \VisualStudioIntegration\Common\Inc\ da instalação do SDK do Visual Studio.  
  
2.  O código a seguir cria um buffer de texto usando o `IVsUserData->GetData()` método. No código a seguir, `pData` é um ponteiro para um `IVsUserData` objeto.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Usando o Editor do Visual Studio serviços em um componente de MEF não  
 Se você tiver um componente existente do código gerenciado que não use MEF e você deseja usar os serviços do editor do Visual Studio, você deve adicionar uma referência ao assembly que contém o ComponentModelHost VSPackage e obter seu serviço SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Para consumir componentes do editor do Visual Studio de um componente não MEF  
  
1.  Adicione uma referência ao assembly Microsoft.VisualStudio.ComponentModelHost.dll em de... \Common7\IDE\ a pasta de instalação do Visual Studio. Verifique se `CopyLocal` é definido como `false`.  
  
2.  Adicionar uma particular `IComponentModel` membro para a classe na qual você deseja usar os serviços de editor do Visual Studio, da seguinte maneira.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Criar uma instância do modelo de componente no método de inicialização para seu componente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Depois disso, você pode obter qualquer um dos serviços do editor do Visual Studio ao chamar o `IComponentModel.GetService<T>()` método para o serviço que desejar.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```