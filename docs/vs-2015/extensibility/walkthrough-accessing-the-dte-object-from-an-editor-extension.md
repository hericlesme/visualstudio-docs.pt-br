---
title: 'Passo a passo: Acessando o objeto DTE de uma extensão do Editor | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91d1683b6c2743df2f04d6462ae0a57ec7b0aff4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466845"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Passo a passo: acessando o objeto DTE de uma extensão do editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [instruções passo a passo: acessando o objeto DTE de uma extensão do Editor](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension).  
  
Em VSPackages, você pode obter o objeto DTE chamando o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método com o tipo do objeto DTE. Nas extensões do Managed Extensibility Framework (MEF), você pode importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e, em seguida, chamar o <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método com um tipo de <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Obtendo o objeto DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Para obter o objeto DTE do provedor de serviços  
  
1.  Crie um projeto de VSIX em C# chamado `DTETest`. Adicione um modelo de item de classificação do Editor e denomine- `DTETest`. Para obter mais informações, consulte [criar uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Adicione as seguintes referências de assembly ao projeto:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Vá até o arquivo DTETest.cs e adicione o seguinte `using` diretivas:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  No `GetDTEProvider` classe, importar um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  No método `GetClassifier()`, adicione o seguinte código.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Se você tiver que usar o <xref:EnvDTE80.DTE2> interface, você pode converter o objeto DTE para ele.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)

