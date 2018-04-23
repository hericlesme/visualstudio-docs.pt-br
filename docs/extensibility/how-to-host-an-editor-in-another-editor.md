---
title: 'Como: hospedar um Editor em outro Editor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 351d66a9ab9b24c53dac4ed070c80f0e51e5e31f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Como: hospedar um Editor em outro Editor
No Visual Studio, você pode hospedar um editor dentro de outro, especificando a janela de hospedagem como uma janela pai. Para fazer isso, defina os parâmetros <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> no quadro de janela filho.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Para configurar o quadro de janela para hospedar um editor  
  
1.  Designe um editor como um editor hospedado por meio da criação de um painel de janela filho.  
  
     Esse painel é aonde texto do editor.  
  
2.  Criar o editor de hospedagem usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> método.  
  
3.  Definir o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> propriedades na implementação do quadro de janela do editor hospedado passando essas propriedades como parâmetros para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> método, respectivamente.  
  
     Se você precisar recuperar esses parâmetros, passar essas propriedades para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.  
  
4.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para o editor independente.  
  
     O editor aparece no painel hospedado do editor do recipiente.  
  
## <a name="robust-programming"></a>Programação robusta  
 O **Application Designer** no Visual Studio Team Edition para arquitetos é um exemplo de um quadro de janela de editor hospedagem outro editor. O **Application Designer** hospeda outros designers no painel direito. Um painel designer (ou **propriedades** página) para cada um dos designers independentes é adicionada ao quadro da janela que contém.