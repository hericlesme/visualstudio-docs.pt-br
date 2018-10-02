---
title: Procure e selecione uma caixa de diálogo do tipo .NET (herdado) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7b20a71b4f38a5cfd4ba8e8de73c8b8fcfd992ef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472700"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Procurar e selecione uma caixa de diálogo de tipo do .NET (legados)
Este tópico descreve como usar o **navegue e selecione um tipo .NET** caixa de diálogo em novas [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 No **propriedades** janela, quando você seleciona as propriedades que usam um tipo .NET Framework em um assembly referenciado, reticências **[...]**  aparece no final da caixa de texto da propriedade. Clicar a **[...]**  abre o **navegue e selecione um tipo .NET** caixa de diálogo. Na caixa de diálogo, você pode escolher um tipo de um modo de exibição de árvore assemblies referenciados. Por exemplo, quando você estiver usando o Designer de atividade na **propriedades** janela, clique no **classe base** elipses **[...]**  para selecionar outra classe base para uma atividade de árvore Assemblies referenciados.  
  
 A tabela a seguir descreve os elementos de (UI) de interface do usuário para o **navegue e selecione um tipo .NET** caixa de diálogo.  
  
|Elemento da Interface do Usuário|Descrição|  
|----------------|-----------------|  
|**Nome do tipo:**|O nome do tipo selecionado.|  
|**Tipo**|O painel esquerdo exibe um modo de exibição de árvore assemblies referenciados. O painel direito exibe os tipos disponíveis para a seleção do assembly referenciado selecionado no painel esquerdo.|  
  
## <a name="see-also"></a>Consulte também  
 [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)