---
title: Designer de fluxo de trabalho - procurar e selecione uma caixa de diálogo de tipo .NET (legados)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 23e311aa8e87fe799bc8ea22a22ffd8e789b3dcd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Procurar e selecione uma caixa de diálogo de tipo do .NET (legados)

Este tópico descreve como usar o **procurar e selecionar um tipo .NET** caixa de diálogo no Designer de fluxo de trabalho herdado do Windows. Use o Designer de fluxo de trabalho herdado quando você precisa direcionar o .NET Framework versão 3.5 ou o WinFX.

 No **propriedades** janela, quando você seleciona propriedades que usam um tipo .NET Framework em um assembly referenciado, um botão de reticências **[...]**  aparece no final da caixa de texto da propriedade. Clique o **[...]**  abre o **procurar e selecionar um tipo .NET** caixa de diálogo. Na caixa de diálogo, você pode escolher um tipo de um modo de exibição de árvore assemblies referenciados. Por exemplo, quando você estiver usando o Designer de atividade no **propriedades** janela, clique no **classe Base** reticências **[...]**  para selecionar outra classe base para uma atividade de árvore de Assemblies referenciados.

 A tabela a seguir descreve os elementos de interface de usuário do **procurar e selecionar um tipo .NET** caixa de diálogo.

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Nome do tipo:**|O nome do tipo selecionado.|
|**Tipo**|O painel esquerdo exibe um modo de exibição de árvore assemblies referenciados. O painel direito exibe os tipos disponíveis para a seleção do assembly referenciado selecionado no painel esquerdo.|

## <a name="see-also"></a>Consulte também

- [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)