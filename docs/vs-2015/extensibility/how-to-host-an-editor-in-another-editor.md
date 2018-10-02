---
title: 'Como: hospedar um Editor em outro Editor | Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6390f5550c445239fbd8f8f72f9c8c4ad013665a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463491"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Como: hospedar um Editor em outro Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: Editor de um Host em outro Editor](https://docs.microsoft.com/visualstudio/extensibility/how-to-host-an-editor-in-another-editor).  
  
No Visual Studio, você pode hospedar um editor dentro de outro, especificando a janela de hospedagem como uma janela pai. Para fazer isso, defina os parâmetros <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> no quadro de janela filho.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Para configurar o quadro de janela para hospedar um editor  
  
1.  Designe um editor como um editor hospedado, criando um painel de janela filho.  
  
     Esse painel é onde irão texto do editor.  
  
2.  Criar o editor de hospedagem usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> método.  
  
3.  Defina a <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> propriedades em que a implementação do quadro de janela do editor hospedado, passando a essas propriedades como parâmetros para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> método, respectivamente.  
  
     Se você precisar recuperar esses parâmetros, passar essas propriedades para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.  
  
4.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para o editor independente.  
  
     O editor aparece no painel hospedado do editor do recipiente.  
  
## <a name="robust-programming"></a>Programação robusta  
 O **Application Designer** no Visual Studio Team Edition for Architects é um exemplo de um quadro de janela do editor outro editor de hospedagem. O **Application Designer** hospeda outros designers em seu painel direito. Um painel do designer (ou **propriedades** página) para cada um dos designers contidos é adicionada ao quadro da janela recipiente.

