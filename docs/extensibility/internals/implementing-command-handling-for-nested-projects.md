---
title: Implementar o tratamento de comando aninhados projetos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e4ed9efab34a51bdfaacea1773a33637437b2ced
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementando o tratamento de projetos aninhados de comando
O IDE pode passar comandos que são passados para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaces para projetos aninhados, ou pai podem filtrar ou substituir os comandos.  
  
> [!NOTE]
>  Somente os comandos que normalmente é tratados pelo projeto pai podem ser filtrados. Comandos como **criar** e **implantar** que são manipuladas pelo IDE não pode ser filtrado.  
  
 As etapas a seguir descrevem o processo para implementar a manipulação de comandos.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-implement-command-handling"></a>Para implementar o tratamento de comando  
  
1.  Quando o usuário seleciona um projeto aninhado ou um nó em um projeto aninhado:  
  
    1.  O IDE chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método.  
  
     – ou —  
  
    1.  Se o comando foi originada em uma janela de hierarquia, como um comando de menu de atalho no Gerenciador de soluções, o IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método pai do projeto.  
  
2.  O projeto pai pode examinar os parâmetros a serem passados para `QueryStatus`, como `pguidCmdGroup` e `prgCmds`, para determinar se o projeto pai deve filtrar os comandos. Se o projeto principal é implementado para comandos de filtragem, deve definir:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     O projeto pai deve retornar `S_OK`.  
  
     Se o projeto pai não filtrar o comando, ele deverá apenas retornar `S_OK`. Nesse caso, o IDE automaticamente encaminha o comando para o projeto filho.  
  
     O projeto pai não tem que rotear o comando para o projeto filho. O IDE executa essa tarefa.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Comandos, Menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Aninhar projetos](../../extensibility/internals/nesting-projects.md)