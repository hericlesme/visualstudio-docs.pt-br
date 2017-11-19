---
title: "Fornecer suporte em um serviço de linguagem de estrutura de tópicos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fd353e39e3e3edbdbdb929fa16abb74126dbbc9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Como: fornecer suporte expandido de estrutura de tópicos em um serviço de linguagem herdado
Há duas opções para estender o suporte da estrutura de tópicos para seu idioma além de oferecer suporte a **recolher definições** comando. Você pode adicionar regiões controlado pelo editor e adiciona regiões de estrutura de tópicos controlado pelo cliente.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Adicionar regiões controlado pelo Editor  
 Use essa abordagem para criar uma região de estrutura de tópicos e, em seguida, permitir que o editor para controlar se a região é expandida, recolhido e assim por diante. Das duas opções para fornecer suporte a estrutura de tópicos, essa opção é menos eficiente. Para essa opção, você deve criar uma nova região de estrutura de tópicos em um intervalo especificado de texto usando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Depois que essa região é criado, seu comportamento é controlado pelo editor. Use o procedimento a seguir para implementar regiões controlado pelo editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar uma região controlado pelo editor de estrutura de tópicos  
  
1.  Chamar `QueryService` para<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando um ponteiro para um buffer de texto especificado. Isso retorna um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto para o buffer.  
  
3.  Chamar <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> para adicionar um ou mais novos regiões de estrutura de tópicos por vez.  
  
     Esse método permite que você especifique o intervalo de texto da estrutura de tópicos, se as regiões de estrutura de tópicos existentes são removidos ou preservados e se a região de estrutura de tópicos é expandida ou recolhida por padrão.  
  
## <a name="adding-client-controlled-outline-regions"></a>Adicionar regiões controlado pelo cliente  
 Use essa abordagem de estrutura de tópicos de implementar controlado pelo cliente (ou inteligente) como que é usado pelo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] serviços de idioma. Um serviço de linguagem que gerencia sua própria estrutura de tópicos monitora o conteúdo do buffer de texto para destruir o antigo regiões de estrutura de tópicos quando eles se torna inválido e crie novas regiões de estrutura de tópicos, conforme necessário.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar uma região de estrutura de tópicos controlado pelo cliente  
  
1.  Chamar `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando um ponteiro para um buffer de texto especificado. Isso determina se o texto oculto já existe uma sessão para o buffer.  
  
3.  Se texto já existe uma sessão, você não precisa criar um e um ponteiro para existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto é retornado. Use esse ponteiro para enumerar e criar regiões de estrutura de tópicos. Caso contrário, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> para criar uma sessão de texto oculto para o buffer. Um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto é retornado.  
  
    > [!NOTE]
    >  Quando você chama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, você pode especificar um cliente do texto oculto (ou seja, um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objeto). Esse cliente notifica você quando um texto oculto ou região de estrutura de tópicos é expandido ou recolhido pelo usuário.  
  
4.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> estrutura) parâmetro: Especifique um valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> no `iType` membro o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura para indicar que você está criando uma região de estrutura de tópicos, em vez de uma região oculta. Especifique se a região é controlado pelo cliente ou controlado por editor no `dwBehavior` membro o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura. A implementação de estrutura de tópicos inteligente pode conter uma mistura de editor e o cliente controlados regiões de estrutura de tópicos. Especifique o texto do banner é exibido quando a região de estrutura de tópicos estiver recolhida, como "...", no `pszBanner` membro o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura. Texto da faixa do editor padrão para uma região oculta é "...".