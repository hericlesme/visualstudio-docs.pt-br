---
title: 'Como: definir e consumir representantes de atividades no Designer de fluxo de trabalho | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fc0964cc6c781c34a4b4cab4ea4901837322c0af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Como: Defina e consumir representantes de atividade em Designer de Fluxo de Trabalho
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] inclui um novo de designer para fora da caixa para atividades de <xref:System.Activities.Statements.InvokeDelegate> . Este criador pode ser usado para atribuir os representantes para a atividade que derivam de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Defina um representante de atividades  
  
1.  Em [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], selecione **arquivo**, **novo**, **projeto**. Selecione o **fluxo de trabalho** nó à esquerda e o **aplicativo de Console do fluxo de trabalho** modelo à direita. Nome do projeto (se desejado) e clique em **Okey**.  
  
2.  Clique com botão direito no projeto no **Solution Explorer** e selecione **adicionar**, **Novo Item...** . Selecione o **fluxo de trabalho** nó à esquerda e o **atividade** modelo à direita. Nomeie a nova atividade **MyForEach.xaml** e clique em **Okey**. A atividade será aberto no designer de fluxo de trabalho.  
  
3.  No designer de fluxo de trabalho, clique o **argumentos** guia.  
  
4.  Clique em **criar argumento**. Nomeie o novo argumento **itens**.  
  
5.  No **tipo de argumento** coluna, selecione **matriz de [T]**.  
  
6.  No navegador de tipo, selecione **objeto**. Click **Ok**.  
  
7.  Clique em **criar argumento** novamente. Nomeie o novo argumento **corpo**. No **direção** coluna para o argumento de novo, selecione **propriedade**.  
  
8.  Na coluna de tipo de argumento, selecione **procurar tipos...**  
  
9. No navegador de tipo, insira **ActivityAction** no **nome do tipo** campo. Selecione **ActivityAction\<T >** na exibição de árvore. Selecione **objeto** na lista suspensa que aparece para atribuir o tipo **ActivityAction\<objeto >** para o argumento.  
  
10. Arraste um <xref:System.Activities.Statements.While> atividade a partir de **fluxo de controle** seção da caixa de ferramentas para a superfície do designer.  
  
11. Selecione o <xref:System.Activities.Statements.While> atividade e selecione o **variáveis** guia.  
  
12. Selecione **criar variável**. Nomeie a nova variável **índice**.  
  
13. No **tipo de variável** coluna, selecione **Int32**. Deixe o **escopo** como **enquanto**e o **padrão** coluna em branco.  
  
14. Definir o **condição** propriedade o <xref:System.Activities.Statements.While> atividade para **índice < Items.Length;**.  
  
15. Arraste um <xref:System.Activities.Statements.InvokeDelegate> atividade do **primitivos** seção da caixa de ferramentas para a **corpo** do <xref:System.Activities.Statements.While> atividade.  
  
16. Selecione **corpo** na lista suspensa delegado.  
  
17. No **propriedades** grade para o <xref:System.Activities.Statements.InvokeDelegate> atividade, clique no **...**  no botão de **argumentos delegado** propriedade.  
  
18. No **valor** coluna do argumento chamado **argumento**, digite **itens [Index]**. Clique em **Okey** para fechar o **DelegateArguments** caixa de diálogo.  
  
19. Arraste uma atividade de <xref:System.Activities.Statements.Assign> na linha horizontal abaixo de atividade de <xref:System.Activities.Statements.InvokeDelegate> . O <xref:System.Activities.Statements.Assign> atividade será criada e um <xref:System.Activities.Statements.Sequence> atividade será criada automaticamente para conter as duas atividades no **corpo** seção o **MyForEach** atividade. A sequência é necessário desde o **corpo** seção só pode conter uma única atividade. Criar automaticamente uma nova atividade de <xref:System.Activities.Statements.Sequence> é um novo recurso de [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
20. Definir o **para** propriedade o <xref:System.Activities.Statements.Assign> atividade para **índice**. Definir o **valor** propriedade o **atribuir** atividade para **índice + 1**.  
  
 Personalizado **MyForEach** atividade agora vai invocar uma atividade arbitrária uma vez para cada valor passado para ele por meio de **itens** coleção, com os valores da coleção como entradas para a atividade.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Use a atividade personalizado em um fluxo de trabalho  
  
1.  Compilar o projeto, pressionando **Ctrl + Shift + B**.  
  
2.  Em **Solution Explorer**, abra **Workflow1.xaml** no designer.  
  
3.  Arraste um **MyForEach** atividade da caixa de ferramentas para a superfície do designer. A atividade será em uma seção da caixa de ferramentas com o mesmo nome que o projeto.  
  
4.  Definir o **itens** propriedade o **MyForEach** atividade para **novo Object [] {1, "abc"}**.  
  
5.  Arraste um <xref:System.Activities.Statements.WriteLine> atividade do **primitivos** seção da caixa de ferramentas para a **delegado: Body** seção o **MyForEach** atividade.  
  
6.  Definir o **texto** propriedade o <xref:System.Activities.Statements.WriteLine> atividade para **Argument.ToString()**.  
  
 Quando o fluxo de trabalho é executado, o console mostrará o seguinte:  
  
 **1**   
**abc**