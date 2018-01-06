---
title: "Comentários para o usuário | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3a5e31eb2acb50d9803bedd77e48d0821cbaea61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="feedback-to-the-user"></a>Comentários para o usuário
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE), comentários visuais sobre funcionalidade disponível é baseada na seleção atual do usuário e o contexto da seleção global. A tabela a seguir lista a funcionalidade que está disponível em contextos de seleção diferente.  
  
|Contexto de seleção|Funcionalidade disponível|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Conjunto de produto atual|Produto específico|  
|Hierarquia ativo|Específico de tipo de hierarquia|  
|Item de hierarquia ativo|Específico de tipo de item de hierarquia|  
|Documento ativo|Específico de tipo de documento|  
|Janela de nível superior interface de documentos múltiplos (MDI)|Específico de tipo de janela|  
|Contexto da seleção atual|Contexto da seleção específico|  
  
 Se você superfície apenas a funcionalidade de usuários precisam e fornecem continuamente os comentários de contexto de ambiente e seleção consistente, você pode reduzir a complexidade no IDE. As seguintes regras se aplicam sempre que uma janela é aberta no IDE:  
  
-   Se a janela altera seu contexto de seleção, comentários de seleção é claramente indicados na janela e a janela Ajuda dinâmica, se ela for exibida, é atualizada para refletir o contexto atual.  
  
-   Se a janela altera o contexto de seleção global, todos os menus de contexto específico, a janela de hierarquia ativo e a barra de título do aplicativo são atualizados para refletir o contexto atual.  
  
-   A janela deve de propriedades para a seleção atual na superfície de **propriedades** janela e, opcionalmente, se ela for exibida, o **páginas de propriedade** caixa de diálogo.  
  
-   Se a janela não superfície propriedades ou alterar o contexto da seleção global, comentários de seleção não devem permanecer na janela quando não é mais a janela ativa no IDE.  
  
-   Todas as janelas de ferramenta específica de documento continuamente devem refletir o documento ativo.  
  
-   Menus, barras de ferramentas e a barra de título do aplicativo devem refletir a janela do cliente superiores interface de documentos múltiplos (MDI).  
  
 Por exemplo, quando o modo de exibição HTML de um formulário da Web dentro de um projeto de aplicativo Web do Visual Basic é aberto e o usuário seleciona um `<td>` marca, comentários é fornecido da seguinte maneira:  
  
-   Seleção é indicada na janela ativa e refletida no **propriedades** janela.  
  
-   Específicos do documento **caixa de ferramentas** é atualizada para refletir o documento ativo.  
  
-   O **Editor** barra de ferramentas e **tabela** menu são exibidas e a barra de título atualizada para refletir a janela de formulário da Web.  
  
-   A janela de hierarquia ativo, o que é normalmente **Solution Explorer**e sua atualização de barra de título para refletir o contexto atual e o contextual **projeto** comandos de menu agora se aplicam à Web ativa Projeto de aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [A seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Objetos de contexto da seleção](../../extensibility/internals/selection-context-objects.md)   
 [Seleção e hierarquias](../../extensibility/internals/hierarchies-and-selection.md)