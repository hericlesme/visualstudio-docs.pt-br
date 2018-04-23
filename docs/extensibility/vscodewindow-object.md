---
title: Objeto VSCodeWindow | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2b1d85eea974e67ae37f8d4d5bfd7aa0069e92b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
Uma janela de código é uma janela de documento especializado que pode incluir uma ou mais exibições de texto, geralmente o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 Em termos de arquitetura, a janela de código é uma janela de documento que está dentro de um quadro de janela. Funcionalmente, a janela de código é simplesmente uma janela de documento com recursos adicionais. No modo de interface de documentos múltiplos (MDI), a janela de código é o quadro de filho MDI. Para obter mais informações, consulte [personalizando janelas de código usando a API herdado](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 A tabela a seguir inclui as interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornece um mecanismo de acesso genérico para localizar um serviço que identifica um identificador global exclusivo (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa um filho de interface MDI vários documentos que contém um ou mais modos de exibição de código.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Preenche um quadro de janela.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Edição de figuras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)