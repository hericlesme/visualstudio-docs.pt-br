---
title: 'Como: implementar o localizar e substituir o mecanismo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26d1866d9b816dfca3f82f98db372865f9d27a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128930"
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