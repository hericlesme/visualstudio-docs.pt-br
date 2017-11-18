---
title: "Como: adicionar comentários a um fluxo de trabalho no Designer de fluxo de trabalho | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: "7"
ms.author: sdanie
manager: erikre
ms.openlocfilehash: 22a96549b70ebf1627b8a94a7c8cd5e2d5835194
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Como: Adicionar comentários a um fluxo de trabalho em Designer de Fluxo de Trabalho
Para facilitar a criação maior, os fluxos de trabalho mais complicados, [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] permitem que o desenvolvedor adiciona anotações aos seguintes tipos de item sobre o designer:  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   Classes derivadas de <xref:System.Activities.Statements.FlowNode>  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  O conteúdo de uma anotação são salvos como texto sem formatação ao arquivo XAML associado com o fluxo de trabalho, e podem potencialmente ser lidas por outro. Seja cuidadoso ao inserir informações sigilosas em uma anotação.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Adicionando uma anotação a uma atividade no designer  
  
1.  No designer de fluxo de trabalho, clique em um item do fluxo de trabalho no designer e selecione **anotações**, **Adicionar anotação**.  
  
2.  Adicione o texto de anotação no espaço fornecido.  
  
3.  O item mostrará um ícone de anotação. Passa sobre o ícone de anotação exibirá o texto de anotação.  
  
     ![Sequência de atividades, mostrando a anotação](../debugger/debug-interface-access/annotation.md "anotação")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Exibindo uma anotação no designer de uma atividade  
  
1.  Com o designer de atividade que tem uma anotação exibindo fora da atividade, clique o **Pin** ícone no adorno de anotação.  
  
2.  A anotação será exibida no designer de atividade. Em captura de tela abaixo, a anotação “que inicia a atividade no fluxo de trabalho” é exibida no designer de atividade.  
  
     ![Anotação mostrada no designer de atividade](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  Para exibir a anotação fora do designer da atividade, passe o mouse sobre a área de anotação no designer da atividade e clique no **Desafixar** ícone  
  
     ![Anotação exibida fora do Designer de uma atividade](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Mostrar ou ocultar todas as anotações  
  
1.  Clique com o botão direito do mouse uma atividade que tenha uma anotação. Selecione **anotações**, **Mostrar todas as anotações**.  
  
2.  Todas as anotações serão exibidas no designer de atividade.  
  
3.  Para exibir todas as anotações fora designers da atividade, clique na atividade e selecione **anotações**, **ocultar todas as anotações**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Editando ou excluindo uma anotação para uma atividade  
  
1.  Clique com o botão direito do mouse em uma atividade que tenha uma anotação.  
  
2.  Selecione **anotações**, **editar anotação** ou **exclusão de anotação**.  
  
3.  A anotação será aberta editando ou excluída.  
  
4.  Para excluir todas as anotações de uma só vez, clique com botão direito do fluxo de trabalho no designer e selecione **anotação**, **excluir todas as anotações**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Adicionando, editar, e excluir uma anotação para uma variável ou um argumento  
  
1.  Clique com o botão direito do mouse em uma variável ou o argumento e selecione adicionar a anotação.  
  
2.  Digite o texto de anotação. A variável ou o argumento exibirá um ícone de anotação.  
  
3.  Clique com o botão direito do mouse em uma variável ou em um argumento que tenha uma anotação. Selecione a anotação de edição.  
  
4.  A anotação será aberta editando.  
  
5.  Clique com o botão direito do mouse em uma variável ou em um argumento que tenha uma anotação. Selecione a anotação excluir.  
  
6.  A anotação será excluída.