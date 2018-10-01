---
title: Contido idiomas | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0b455a526bf1b32de90588a103c23855e730946
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472616"
---
# <a name="contained-languages"></a>Idiomas independentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

A versão mais recente deste tópico pode ser encontrada em [idiomas contidos](https://docs.microsoft.com/visualstudio/extensibility/contained-languages).  
  
*Contido idiomas* são linguagens que são contidas por outras linguagens. Por exemplo, o HTML no [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] páginas podem conter [!INCLUDE[csprcs](../includes/csprcs-md.md)] ou [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] scripts. Uma arquitetura de linguagem dual é necessária para o editor de arquivo. aspx fornecer o IntelliSense, coloração e outros recursos de edição para o HTML e a linguagem de script.  
  
## <a name="implementation"></a>Implementação  
 A interface mais importante que você precisa implementar para idiomas independentes é a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Essa interface é implementada por qualquer linguagem que pode ser hospedada em um idioma principal. Ele fornece acesso para o serviço de linguagem colorizador, filtro de exibição de texto e ID de serviço de idioma primário. O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> permite que você crie um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. As etapas a seguir mostram como implementar uma linguagem independente:  
  
1.  Use `QueryService()` para obter o idioma, ID de serviço e a ID de interface da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> método para criar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Passar uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface, um ou mais [IDs de item](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) e um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface.  
  
3.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface, que é o objeto de coordenador de buffer de texto, fornece os serviços básicos que são necessárias para mapear os locais em um arquivo primário no buffer do idioma secundário.  
  
     Por exemplo, um único arquivo. aspx, o arquivo primário inclui o ASP, HTML e todo o código que está contido. No entanto, o buffer secundário, inclui apenas o código contido, junto com quaisquer definições de classe, para tornar o buffer secundário de um arquivo de código válido. O coordenador de buffer manipula o trabalho de coordenação de edições de um buffer para outro.  
  
4.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> método, que é o idioma principal, informa o coordenador de buffer que texto dentro de seu buffer é mapeado para o texto correspondente em um buffer secundário.  
  
     A linguagem passa uma matriz do <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> estrutura, que atualmente inclui apenas um primário e um secundário span.  
  
5.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> método e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> método fornece o mapeamento do primário para um buffer secundário e vice-versa.

