---
title: "Lista de verificação: Criar um serviço de linguagem herdado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b09176efca3a8839d5e6a741a1e161ff61cdc7ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="checklist-creating-a-legacy-language-service"></a>Lista de verificação: Criar um serviço de linguagem herdado
A lista de verificação a seguir resume as etapas básicas que você deve executar para criar um serviço de idioma para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor de núcleo. Integre seu serviço de idioma em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você deve criar um avaliador de expressão de depuração. Para obter mais informações, consulte [escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) no [extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Etapas para criar um serviço de linguagem  
  
1.  Implementar a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   No seu VSPackage, implementar a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface para fornecer o serviço de linguagem.  
  
    -   Tornar o seu serviço de linguagem disponíveis para o ambiente de desenvolvimento integrado (IDE) no seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementação.  
  
2.  Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface na classe de serviço de idioma principal.  
  
     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface é o ponto inicial da interação entre o editor de núcleo e o serviço de linguagem.  
  
### <a name="optional-features"></a>Recursos opcionais  
 Os recursos a seguir são opcionais e podem ser implementados em qualquer ordem. Esses recursos aumentam a funcionalidade de seu serviço de linguagem.  
  
-   Coloração de sintaxe  
  
     Implementar a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. A implementação desta interface deve as informações de analisador para retornar as informações de cor apropriado.  
  
     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método retorna o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface. Uma instância de colorizador separado é criada para cada buffer de texto, portanto você deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface separadamente. Para obter mais informações, consulte [coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Janela de código  
  
     Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface para habilitar o serviço de linguagem receber notificações de criação de uma nova janela de código.  
  
     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método retorna o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface. O serviço de linguagem pode então adicionar especial da interface do usuário para a janela de código no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. O serviço de linguagem também pode fazer qualquer processamento especial, como adicionar um filtro de exibição de texto em <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   Filtro de exibição de texto  
  
     Para fornecer o IntelliSense a conclusão de instrução em um serviço de linguagem, interceptar alguns dos comandos que trataria a exibição de texto. Para interceptar esses comandos, conclua as seguintes etapas:  
  
    -   Implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> participar os comandos de editor de cadeia e o identificador de comando.  
  
    -   Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método e passar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementação.  
  
    -   Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> método ao desanexar do modo de exibição para que esses comandos não são transmitidos para você.  
  
     Comandos que devem ser tratados dependem de serviços que são fornecidos. Para obter mais informações, consulte [comandos importantes para filtros do serviço de linguagem](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface deve ser implementada no mesmo objeto, como o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
-   Conclusão da instrução  
  
     Implementar a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
     Oferece suporte a comandos de conclusão de instrução (ou seja, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) e chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface, passando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface. Para obter mais informações, consulte [conclusão de instrução em um serviço de linguagem herdado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Dicas de método  
  
     Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface para fornecer dados para a janela de dica de método.  
  
     Instale o filtro de exibição de texto para lidar com comandos adequadamente, para que você saiba quando mostrar uma janela de dica de dados do método. Para obter mais informações, consulte [informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Marcadores de erro  
  
     Implementar a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
     O erro de criação de objetos de marcador que implementam o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface e chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método, passando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface do objeto de marcador de erro.  
  
     Normalmente, cada marcador de erro gerencia um item na janela lista de tarefas.  
  
-   Itens de lista de tarefas  
  
     Implementar uma classe de item de tarefa fornecendo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interface.  
  
     Implementar uma classe de provedor de tarefa fornecendo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interface e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interface.  
  
     Implementar uma classe de enumerador de tarefa fornecendo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interface.  
  
     Registre o provedor de tarefa com a lista de tarefas <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> método.  
  
     Obter o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface chamando o provedor de serviço do serviço de linguagem com o GUID do serviço <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Criar objetos de item de tarefa e chamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> método no <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface quando há novos ou atualizados tarefas.  
  
-   Itens de tarefas de comentário  
  
     Use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interface e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interface para obter o comentário tokens de tarefa.  
  
     Obter um <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> de interface do <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> service.  
  
     Obter o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> de interface do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> método.  
  
     Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interface para escuta de alterações na lista de token.  
  
-   Estrutura de tópicos  
  
     Há várias opções para dar suporte a estrutura de tópicos. Por exemplo, você pode dar suporte a **recolher definições** de comando, forneçam controlado pelo editor de regiões ou regiões controlado pelo cliente. Para obter mais informações, consulte [como: fornecer expandido de estrutura de tópicos suporte em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Registro do serviço de linguagem  
  
     Para obter mais informações sobre como registrar um serviço de idioma, consulte [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service2.md) e [Gerenciando VSPackages](../../extensibility/managing-vspackages.md).  
  
-   Ajuda contextual  
  
     Fornece contexto para o editor de uma das seguintes maneiras:  
  
    -   Fornecer contexto para marcadores de texto com a implementação de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface.  
  
 Fornece todo o contexto de usuário ao implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface.  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)