---
title: "Navegue e selecione uma caixa de diálogo de tipo .NET (legados) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3cdc5d3928cd436d86d529e667f99251e1e7cc95
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Procurar e selecione uma caixa de diálogo de tipo do .NET (legados)
Este tópico descreve como usar o **procurar e selecionar um tipo .NET** caixa de diálogo no Designer de fluxo de trabalho herdado do Windows. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 No **propriedades** janela, quando você seleciona propriedades que usam um tipo .NET Framework em um assembly referenciado, um botão de reticências **[...]**  aparece no final da caixa de texto da propriedade. Clique o **[...]**  abre o **procurar e selecionar um tipo .NET** caixa de diálogo. Na caixa de diálogo, você pode escolher um tipo de um modo de exibição de árvore assemblies referenciados. Por exemplo, quando você estiver usando o Designer de atividade no **propriedades** janela, clique no **classe Base** reticências **[...]**  para selecionar outra classe base para uma atividade de árvore de Assemblies referenciados.

 A tabela a seguir descreve os elementos de interface de usuário do **procurar e selecionar um tipo .NET** caixa de diálogo.

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Nome do tipo:**|O nome do tipo selecionado.|
|**Tipo**|O painel esquerdo exibe um modo de exibição de árvore assemblies referenciados. O painel direito exibe os tipos disponíveis para a seleção do assembly referenciado selecionado no painel esquerdo.|

## <a name="see-also"></a>Consulte também

- [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)