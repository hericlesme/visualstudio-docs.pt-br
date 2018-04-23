---
title: Interfaces de serviço de linguagem herdada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2861c4d6307442e1650b44d2b15f2a084ac7715
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-interfaces"></a>Interfaces de serviço de linguagem herdada
Para qualquer linguagem de programação específica, pode haver apenas uma instância de um serviço de idioma por vez. Entretanto, um serviço de idioma único pode atender mais de um editor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não associar a um serviço de idioma com qualquer editor específico. Portanto, quando você solicita uma operação de serviço de idioma, você deve identificar o editor apropriado como um parâmetro.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Interfaces comuns associados aos serviços de linguagem  
 O editor obtém seu serviço de linguagem chamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> sobre o VSPackage apropriado. O SID (ID) passado na chamada de serviço identifica o serviço de idioma que está sendo solicitado.  
  
 Você pode implementar as interfaces do serviço de idioma principal em qualquer número de classes separadas. No entanto, uma abordagem comum é implementam as interfaces a seguir em uma única classe:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcional)  
  
 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface deve ser implementada em todos os serviços de idioma. Ele fornece informações sobre o serviço de linguagem, como o nome localizado do idioma, as extensões de nome de arquivo associados com o serviço de linguagem e como recuperar um colorizador.  
  
## <a name="additional-language-service-interfaces"></a>Interfaces de serviço de idioma adicionais  
 Outras interfaces podem ser fornecidos com o serviço de linguagem. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicita uma instância separada dessas interfaces para cada instância do buffer de texto. Portanto, você deve implementar cada uma das interfaces em seu próprio objeto. A tabela a seguir mostra as interfaces que exigem uma instância por instância de buffer de texto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gerencia adornos de janela de código, como a barra de menu suspenso. Você pode obter essa interface usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método. Há um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> por janela de código.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colore delimitadores e palavras-chave. Você pode obter essa interface usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> é chamado em tempo de pintura. Evite o trabalho de computação intensa dentro de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ou o desempenho pode ser afetado.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornece dicas de ferramenta de parâmetro de IntelliSense. Quando o serviço de linguagem reconhece um caractere que indica que dados do método deve ser exibido como um parêntese de abertura, ele chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> método para notificar o texto de exibição do serviço de linguagem está pronto para exibir uma dica de ferramenta de informações do parâmetro. A exibição de texto, em seguida, a chamada no serviço de linguagem usando os métodos do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface para obter as informações necessárias para exibir a dica de ferramenta.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fornece preenchimento de instruções IntelliSense. Quando o serviço de idioma está pronto para exibir uma lista de conclusão, ele chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método no modo de texto. A exibição de texto, em seguida, a chamada no serviço de linguagem usando métodos no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objeto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite a modificação do modo de exibição de texto usando o manipulador de comandos. A classe na qual você implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface deverá implementar também a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Recupera o modo de exibição de texto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto consultando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que é passado para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método. Deve haver um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto para cada modo de exibição.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta comandos que o usuário digita na janela de código. Monitorar a saída da sua <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementação para fornecer informações de conclusão personalizado e exibir modificação<br /><br /> Para passar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto para o modo de exibição de texto, chamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Lista de verificação: Criar um serviço de linguagem herdado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)