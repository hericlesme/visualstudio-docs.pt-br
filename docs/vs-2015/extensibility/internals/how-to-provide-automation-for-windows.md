---
title: 'Como: fornecer automação para Windows | Microsoft Docs'
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
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6fad49e2841186cea677a165bdb48c4a1af5b41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466429"
---
# <a name="how-to-provide-automation-for-windows"></a>Como: fornecer automação para Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: fornecer automação para Windows](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-provide-automation-for-windows).  
  
Você pode fornecer automação para janelas de documento e ferramenta. Fornecer automação é recomendável sempre que você deseja disponibilizar os objetos de automação em uma janela, e o ambiente já não fornecem um objeto de automação prontas para uso, como ocorre com uma lista de tarefas.  
  
## <a name="automation-for-tool-windows"></a>Automação para ferramenta Windows  
 O ambiente fornece automação em uma janela de ferramentas, retornando um padrão <xref:EnvDTE.Window> objeto conforme explicado no procedimento a seguir:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Fornecer automação para janelas de ferramentas  
  
1.  Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método por meio do ambiente com <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> como `VSFPROPID` para obter o `Window` objeto.  
  
2.  Quando um chamador solicita um objeto de automação de VSPackage específico para sua janela da ferramenta por meio <xref:EnvDTE.Window.Object%2A>, as chamadas de ambiente `QueryInterface` para `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, ou o `IDispatch` interfaces. Ambos `IExtensibleObject` e `IVsExtensibleObject` fornecem um <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> método.  
  
3.  Quando o ambiente, em seguida, chama o `GetAutomationObject` método passando `NULL`, responder, passando de volta o objeto específico do VSPackage.  
  
4.  Se chamar `QueryInterface` para `IExtensibleObject` e `IVsExtensibleObject` falhar, então, o ambiente chama `QueryInterface` para `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automação para Windows de documento  
 Um padrão <xref:EnvDTE.Document> objeto também está disponível no ambiente, embora um editor pode ter sua própria implementação do `T:EnvDTE.Document` objeto implementando `IExtensibleObject` interface e respondendo a `GetAutomationObject`.  
  
 Além disso, um editor pode fornecer um objeto de automação específicos de VSPackage, recuperado por meio de <xref:EnvDTE.Document.Object%2A> método, Implementando o `IVsExtensibleObject` ou `IExtensibleObject` interfaces. O [exemplos de VSSDK](../../misc/vssdk-samples.md) contribui com um objeto de automação específicos do documento RTF.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>

