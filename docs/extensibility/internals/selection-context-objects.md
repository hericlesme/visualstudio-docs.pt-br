---
title: Objetos de contexto da seleção | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04ccc4a57ac7af144c134761119433b7533e9bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131253"
---
# <a name="selection-context-objects"></a>Objetos de contexto da seleção
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) usa um objeto de contexto global de seleção para determinar o que deve ser exibido no IDE. Cada janela no IDE pode ter seu próprio objeto de contexto de seleção enviada por push para o contexto da seleção global. O IDE atualiza o contexto da seleção global com valores de uma janela quando a janela tem o foco. Para obter mais informações, consulte [comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md).  
  
 Cada site no IDE ou quadro de janela tem um serviço chamado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. O objeto criado pelo seu VSPackage que é localizado no quadro da janela deve chamar o `QueryService` método para obter um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface.  
  
 Janelas com moldura podem manter partes de suas informações de contexto da seleção sejam propagadas para o contexto da seleção global quando eles são iniciados. Essa capacidade é útil para janelas de ferramenta que pode ser necessário iniciar com uma seleção vazia.  
  
 Modificar seleção global contexto aciona eventos VSPackages pode monitorar. VSPackages pode executar as seguintes tarefas ao implementar `IVsTrackSelectionEx` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfaces:  
  
-   Atualize o arquivo atualmente ativo em uma hierarquia.  
  
-   Monitore as alterações a determinados tipos de elementos. Por exemplo, se seu VSPackage usa um especial **propriedades** janela, você pode monitorar as alterações no active **propriedades** janela e reinicie sua quando necessário.  
  
 A sequência a seguir mostra o curso típico de controle de seleção.  
  
1.  O IDE recupera o contexto da seleção da janela recém-aberta e o coloca no contexto de seleção global. Se o contexto da seleção usa HIERARCHY_DONTPROPAGATE ou SELCONTAINER_DONTPROPAGATE, essas informações não são propagadas para o contexto global. Para obter mais informações, consulte [comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Eventos de notificação são transmitidos para qualquer VSPackage que solicitou.  
  
3.  O VSPackage age sobre os eventos que ele recebe pela execução de atividades, como atualização de uma hierarquia, reativando uma ferramenta ou outras tarefas semelhantes.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [A seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Tipos de projeto](../../extensibility/internals/project-types.md)