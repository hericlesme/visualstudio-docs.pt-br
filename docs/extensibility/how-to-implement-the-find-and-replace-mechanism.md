---
title: 'Como: implementar o localizar e substituir o mecanismo | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c12e300a3537d1927710b0a4c3550ec3f5fd762
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Como: implementar o localizar e substituir o mecanismo
O Visual Studio fornece duas maneiras de localizar/substituir a implementação. É uma maneira passar uma imagem de texto para o shell e deixá-lo a lidar com a pesquisa, realce e substituir texto. Isso permite aos usuários especificar vários intervalos de texto. Como alternativa, o VSPackage pode controlar essa funcionalidade em si. Em ambos os casos, você deve notificar o shell sobre o destino atual e os destinos de todos os documentos abertos.  
  
### <a name="to-implement-findreplace"></a>Para implementar localizar/substituir  
  
1.  Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interface em um dos objetos retornados pelas propriedades do quadro <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> ou <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Se você estiver criando um editor personalizado, você deve implementar essa interface como parte da classe de editor personalizado.  
  
2.  Use o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> método para especificar as opções que dá suporte a seu editor e indicar se ele implementa a pesquisa de texto imagem.  
  
     Se seu editor dá suporte à busca de imagens de texto, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     Caso contrário, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Se você implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> métodos, você pode simplificar as tarefas de pesquisa chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interface.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>