---
title: "A seleção e moeda no IDE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 307344a9027e629f08350b77adf99d22d0c127a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="selection-and-currency-in-the-ide"></a>A seleção e moeda no IDE
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) mantém informações sobre dos usuários objetos selecionados no momento usando a seleção *contexto*. Com o contexto de seleção VSPackages pode fazer parte de moeda de controle de duas maneiras:  
  
-   Propagando as informações de moeda sobre VSPackages ao IDE.  
  
-   Monitorando as seleções de usuários atualmente ativos dentro do IDE.  
  
## <a name="selection-context"></a>Contexto de seleção  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalmente mantém o controle de moeda IDE no seu próprio objeto de contexto da seleção global. A tabela a seguir mostra os elementos que compõem o contexto da seleção.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Hierarquia atual|Normalmente, o projeto atual; uma hierarquia atual NULL indica que a solução como um todo é atual.|  
|ItemID atual|O item selecionado dentro da hierarquia atual; Quando há várias seleções em uma janela de projeto, pode haver vários itens atuais.|  
|Atual`SelectionContainer`|Contém um ou mais objetos para que a janela de propriedades deve exibir propriedades.|  
  
 Além disso, o ambiente mantém duas listas globais:  
  
-   Uma lista de identificadores de comando de interface do usuário ativas  
  
-   Uma lista de tipos de elementos ativos atualmente.  
  
### <a name="window-types-and-selection"></a>Seleção e tipos de janelas  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organiza windows em dois tipos gerais:  
  
-   Windows do tipo de hierarquia  
  
-   Janelas com moldura, como janelas de ferramenta e de documentos  
  
 O IDE rastreia moeda diferente para cada um desses tipos de janela.  
  
 A janela de tipo de projeto mais comum é o Gerenciador de soluções, que controla o IDE. Uma janela de tipo de projeto controla a hierarquia global e ItemID do contexto da seleção global e a janela se baseia na seleção do usuário para determinar a hierarquia atual. Para windows de tipo de projeto, o ambiente fornece o serviço global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>por quais VSPackages pode monitorar os valores atuais de elementos abertos. Propriedade de navegação no ambiente é orientada por este serviço global.  
  
 Janelas com moldura, por outro lado, usam o DocObject dentro da janela do quadro para enviar por push o valor de SelectionContext (os três componentes ItemID/hierarquia/SelectionContainer). . Janelas com moldura usam o serviço <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para essa finalidade. O DocObject pode enviar por push somente os valores para o contêiner de seleção, deixando os valores de locais para a hierarquia e ItemID inalterados, que é típico para documentos de filho MDI.  
  
### <a name="events-and-currency"></a>Eventos e moeda  
 Dois tipos de eventos podem ocorrer que afetam a noção do ambiente de moeda:  
  
-   Eventos que são propagados para o nível global e alterar o contexto de seleção do quadro de janela. Esse tipo de evento exemplos de uma janela filho MDI está sendo aberta, uma janela de ferramentas global que está sendo aberto ou uma janela de ferramenta do tipo de projeto que está sendo aberto.  
  
-   Eventos que alteram os elementos rastreados dentro do contexto de seleção do quadro de janela. Exemplos incluem alterar seleção dentro de um DocObject ou alterar a seleção em uma janela de tipo de projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Objetos de contexto da seleção](../../extensibility/internals/selection-context-objects.md)   
 [Comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md)