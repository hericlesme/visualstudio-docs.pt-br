---
title: 'Como: dar suporte a estrutura de tópicos em um serviço de linguagem herdado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9880c5c255118478d15f34f9a9245a1c25d97fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130228"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Como: dar suporte a estrutura de tópicos em um serviço de linguagem herdado
Estrutura de tópicos é usada para expandir ou recolher as regiões diferentes de texto. O modo de estrutura de tópicos é usada pode ser definido de forma diferente por diferentes idiomas. Para obter mais informações, consulte [Estrutura de tópicos](../../ide/outlining.md).  
  
 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar a estrutura de tópicos, consulte [passo a passo: estrutura de tópicos](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso melhorar o desempenho do seu serviço de linguagem e permitem que você aproveite os novos recursos do editor.  
  
 A seguir demonstra como dar suporte a esse comando para o serviço de linguagem.  
  
### <a name="to-support-outlining"></a>Para dar suporte a estrutura de tópicos  
  
1.  Implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> em seu objeto de serviço de linguagem.  
  
2.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> no objeto de sessão de estrutura de tópicos atual para adicionar novas regiões de estrutura de tópicos.  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando um usuário seleciona **recolher para definições** no **estrutura de tópicos** menu, as chamadas IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> em seu serviço de linguagem.  
  
 Quando este método é chamado, o IDE passa um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> ponteiro (um ponteiro para um buffer de texto) e um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (um ponteiro para a sessão atual de estrutura de tópicos).  
  
 Você pode chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> método para várias regiões de estrutura de tópicos especificando essas regiões no `rgOutlnReg` parâmetro. O `rgOutlnReg` parâmetro é um <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> estrutura. Esse processo permite que você especifique as características diferentes de região oculta, como se uma determinada região é expandida ou recolhida.  
  
> [!NOTE]
>  Tenha cuidado ao ocultar caracteres de nova linha. Texto oculto deve estender desde o início da primeira linha para o último caractere da última linha em uma seção, deixando o caractere de nova linha final visíveis.  
  
## <a name="see-also"></a>Consulte também  
 [Como: fornecer suporte a texto oculto em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Como fornecer suporte estendido à estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)