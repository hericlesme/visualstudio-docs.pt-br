---
title: 'Como: adicionar um novo Item a um projeto de fluxo de trabalho (legados) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1699b3f2d16bb481a7efb744eed58d395dbc8773
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Como: Adicionar um novo item em um fluxo de trabalho Project (o legados)
Depois de criar um projeto de fluxo de trabalho usando o Designer de fluxo de trabalho herdado do Windows fornecida pelo [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] que tem como alvo o o [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], você pode adicionar [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] itens e outros familiar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] itens de sua projeto.

 A tabela a seguir lista os itens de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] que você pode adicionar a um projeto de fluxo de trabalho.

|Item|Descrição|
|----------|-----------------|
|Atividade|Uma atividade com a definição de atividade em um código de arquivo e de usuário do designer de código em um código separado arquivos.|
|Atividade (com separação de código)|Uma definição de atividade expressa como a marcação de fluxo de trabalho e o código do usuário em um arquivo separado código.|
|Fluxo de trabalho sequencial (código)|Um trabalho sequenciais com a definição de trabalho em um código de arquivo e de usuário do designer de código em um arquivo separado código.|
|Fluxo de trabalho sequencial (com separação de código)|Um trabalho sequenciais com a definição de trabalho expressa como a marcação de fluxo de trabalho e o código do usuário em um arquivo separado código.|
|Fluxo de trabalho do computador de estado (código)|Um trabalho do computador de estado com a definição de trabalho em um código de arquivo e de usuário do designer de código em um arquivo separado código.|
|Fluxo de trabalho do computador de estado (com separação de código)|Um trabalho do computador de estado com a definição de trabalho expressa como a marcação de fluxo de trabalho e o código do usuário em um arquivo separado código.|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Para adicionar um novo item em um fluxo de trabalho projeto

1.  Sobre o **projeto** menu, clique em **adicionar um novo Item**.

     O **adicionar um novo Item** caixa de diálogo é aberta.

2.  Selecione um item.

     A tabela anterior lista opções disponíveis do Windows Workflow Foundation.

3.  Clique em **adicionar** para adicionar o item ao projeto de fluxo de trabalho.

## <a name="see-also"></a>Consulte também

- [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)