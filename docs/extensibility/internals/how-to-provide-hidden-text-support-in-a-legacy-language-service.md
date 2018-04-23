---
title: 'Como: fornecer suporte a texto oculto em um serviço de linguagem herdado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54e508c6bcbb9cb79459e0b61a97f51350c00708
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Como: fornecer suporte a texto oculto em um serviço de linguagem herdado
Você pode criar regiões de texto oculto além das regiões de estrutura de tópicos. Regiões do texto oculto podem ser controlado pelo cliente ou controlada pelo editor e são usados para ocultar uma região do texto completamente. O editor exibe uma região oculta como linhas horizontais. Um exemplo disso é o modo de exibição somente Script no editor de HTML.  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-implement-a-hidden-text-region"></a>Para implementar uma região do texto oculto  
  
1.  Chamar `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando um ponteiro para um buffer de texto especificado. Isso determina se o texto oculto já existe uma sessão para o buffer.  
  
3.  Se já existir, você não precisa criar um e um ponteiro para existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto é retornado. Use esse ponteiro para enumerar e criar regiões de texto oculto. Caso contrário, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> para criar uma sessão de texto oculto para o buffer.  
  
     Um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto é retornado.  
  
    > [!NOTE]
    >  Quando você chama `CreateHiddenTextSession`, você pode especificar um cliente do texto oculto (ou seja, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). O cliente do texto oculto notifica quando o texto oculto ou estrutura de tópicos é expandida ou recolhida pelo usuário.  
  
4.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> adicionar um ou mais novos descrever regiões por vez, especifique as seguintes informações no `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parâmetro:  
  
    1.  Especifique um valor de `hrtConcealed` no `iType` membro o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura para indicar que você está criando uma região oculta, em vez de uma região de estrutura de tópicos.  
  
        > [!NOTE]
        >  Quando regiões oculto estiverem ocultas, o editor exibe automaticamente linhas ao redor das regiões ocultas para indicar sua presença.  
  
    2.  Especifique se a região é controlado pelo cliente ou controlado por editor no `dwBehavior` membros o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura. Sua implementação de estrutura de tópicos inteligente pode conter uma mistura de estrutura de tópicos do editor e o cliente controlados e regiões de texto oculto.