---
title: Personalização do Windows de código usando a API herdado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8284985003415ef3e723fe735e64481c3666180a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personalização do Windows de código usando a API herdado
Uma janela de código é um objeto de janela de documento que oferece suporte a um ou mais modos de exibição de texto. Os recursos exatos de uma janela de código dependem do serviço de idioma associado. No modo de interface de documentos múltiplos (MDI), a janela de código é o quadro de filho MDI.  
  
 Janelas de código são controladas pelos serviços de idioma, e cada serviço de linguagem pode fornecer seu próprio Gerenciador de janela de código. Isso permite que o serviço de linguagem adicionar seus próprio adornos para a janela de código, como linhas onduladas, colorização e muito mais. Para obter mais informações sobre como criar uma janela principal, consulte [instanciar o núcleo Editor usando a API herdado](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Uma janela de código é um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto que tem uma exibição de texto e qualquer ornamentos localizados no objeto. Quando você criar a janela de código durante a instanciação do núcleo do editor, o serviço de linguagem pode anexar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> para a janela de código, como é mostrado na ilustração a seguir.  
  
 ![Gráfico de CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Janela de código  
  
 O serviço de linguagem implementa o Gerenciador de janelas de código e é responsável por gerenciar ornamentos, como uma barra de menu suspenso. A janela de código chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> método durante a inicialização da janela de código. Quando essa chamada é feita, o serviço de linguagem pode adicionar uma barra de menu suspenso ou uma barra de botões (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) para a janela de código.  
  
## <a name="in-this-section"></a>Nesta seção  
 `Customizing Code Windows by Using the Legacy API`  
 Explica como personalizar as janelas de código usando a API herdada.  
  
 [Como: hospedar um Editor em outro Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explica como hospedar um segundo editor dentro de uma janela do editor.  
  
 [Como: disparar eventos quando o Editor perde o foco](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explica como anexar um modo de exibição de documentos para um objeto de dados de documento.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Criando o Editor de núcleo usando a API herdado](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Acessando theText exibição usando a API herdado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)