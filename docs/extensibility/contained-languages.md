---
title: Contidos idiomas | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7ec180689f4dadfb60832259ddee51a05f336fda
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="contained-languages"></a>Idiomas independentes

*Contidos idiomas* idiomas que estão contidas em outros idiomas. Por exemplo, HTML em [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] páginas podem conter [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] scripts. Uma arquitetura dual idioma é necessária para o editor de arquivo. aspx fornecer o IntelliSense, a colorização e outros recursos de edição de HTML e a linguagem de script.

## <a name="implementation"></a>Implementação

A interface mais importante que você precisa implementar para idiomas independentes é a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Essa interface é implementada por todos os idiomas que podem ser hospedados em um idioma principal. Ele fornece acesso para o serviço de linguagem colorizador, filtro de exibição de texto e ID de serviço de idioma primário. O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> permite que você crie um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. As etapas a seguir mostram como implementar uma linguagem independente:

1.  Use `QueryService()` para obter o idioma, ID de serviço e a ID de interface do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Para criar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface, chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> método. Passar um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface, um ou mais [de item IDs](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)e um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface.

3.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface, que é o objeto de coordenador de buffer de texto, fornece os serviços básicos que são necessárias para mapear locais em um arquivo primário no buffer do idioma secundário.

     Por exemplo, em um arquivo. aspx único, o arquivo primário inclui o ASP, HTML e todo o código que está contido. No entanto, o buffer secundário inclui apenas o código independente juntamente com quaisquer definições de classe, para tornar o buffer secundário um arquivo de código válido. O coordenador de buffer manipula o trabalho de coordenação de edições de um buffer para o outro.

4.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> método, que é o idioma principal, informa o coordenador de buffer o texto dentro de seu buffer é mapeado para o texto correspondente no buffer secundário.

     O idioma passa uma matriz do <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> estrutura, que atualmente inclui somente um principal e um secundário alcance.

5.  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> método e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> método fornece o mapeamento do primário para o buffer secundária e vice-versa.