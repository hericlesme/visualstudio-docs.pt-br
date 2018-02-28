---
title: Tratamento de comandos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3ecbff62570067b25aae9ad525138687eb281c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="command-handling"></a>Tratamento de comandos
O editor pode definir novos comandos. Normalmente, os comandos são exibidos em um menu em uma barra de ferramentas ou em um menu de contexto.  
  
 Para obter mais informações sobre como definir os menus e comandos, consulte [comandos, Menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Um serviço de idioma pode controlar quais menus de contexto são mostrados no editor, interceptando a <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeração. Como alternativa, você pode controlar o menu de contexto em uma base por marcador. Para obter mais informações, consulte [comandos importantes para filtros do serviço de linguagem](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Adicionando comandos ao Menu de contexto do Editor  
 Para adicionar um comando no menu de contexto, você deve primeiro definir um conjunto de comandos de menu que pertencem a um grupo específico. O exemplo a seguir é retirado do arquivo. VSCT gerado como parte do passo a passo [passo a passo: adicionando recursos para um Editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Guid de menu = "guidCustomEditorCmdSet" id = "IDMX_RTF" prioridade = "0x0000" type = "Context" >  
  
 \<Guid do pai = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Cadeias de caracteres >  
  
 \<ButtonText > Menu de contexto CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Cadeias de caracteres >  
  
 \</ Menu >  
  
 \</ Menus >  
  
 O texto acima adiciona um comando de menu de contexto com o texto **Menu de contexto CustomEditor**. O GUID de Menu é que o do conjunto de comando que é criado com este editor e o tipo for "Context".  
  
 Você também pode usar comandos predefinidos que não precisam ser definidos no arquivo. VSCT. Por exemplo, se você examinar o arquivo EditorPane.cs gerado pelo modelo de pacote do Visual Studio, você descobrir que um conjunto de comandos predefinidos, como <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definido pela <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, são tratados em manipuladores de comandos, como o método onSelectAll.  
  
## <a name="see-also"></a>Consulte também  
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)