---
title: 'Passo a passo: Acessando o objeto DTE de uma extensão de Editor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b888136f51e7893c6ad44ab888d8079ee92d8edf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Passo a passo: Acessando o objeto DTE de uma extensão de Editor
Em VSPackages, você pode obter o objeto DTE chamando o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método com o tipo do objeto DTE. Nas extensões do Managed Extensibility Framework (MEF), você pode importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e, em seguida, chame o <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método com um tipo de <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Obtendo o objeto DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Para obter o objeto DTE do provedor de serviços  
  
1.  Crie um projeto c# VSIX denominado `DTETest`. Adicione um modelo de item de classificação de Editor e denomine- `DTETest`. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Adicione as seguintes referências de assembly ao projeto:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Vá para o arquivo DTETest.cs e adicione o seguinte `using` diretivas:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  No `GetDTEProvider` classe, importe um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  No método `GetClassifier()`, adicione o seguinte código.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Se você precisar usar o <xref:EnvDTE80.DTE2> interface, você pode converter o objeto DTE para ele.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)