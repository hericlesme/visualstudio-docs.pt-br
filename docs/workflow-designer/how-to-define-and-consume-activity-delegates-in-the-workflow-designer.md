---
title: 'Designer de fluxo de trabalho - como: definir e consumir representantes de atividade'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2039c1792a5e42c3181a01b10ff5bf271ea3bf2f
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755750"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Como: Defina e consumir representantes de atividade em Designer de Fluxo de Trabalho

.NET framework 4.5 inclui um designer de out-of-box para o <xref:System.Activities.Statements.InvokeDelegate> atividade. Este criador pode ser usado para atribuir os representantes para a atividade que derivam de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Defina um representante de atividades

1.  No Visual Studio, selecione **arquivo** > **New** > **projeto**.

1. No **novo projeto** caixa de diálogo, selecione o **fluxo de trabalho** categoria à esquerda e, em seguida, selecione o **aplicativo de Console do fluxo de trabalho** modelo de projeto. Nomeie o projeto (se desejado) e clique em **Okey**.

   > [!NOTE]
   > Se você não vir as **fluxo de trabalho** categoria, primeiro instale o **Windows Workflow Foundation** componente do Visual Studio 2017. Para obter instruções detalhadas, consulte [instalar o Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

2.  Clique com botão direito no projeto no **Gerenciador de soluções** e selecione **Add** > **Novo Item**. Selecione o **fluxo de trabalho** categoria e, em seguida, selecione o **atividade** modelo de item. Nomeie a nova atividade **Myforeach** e, em seguida, selecione **Okey**.

   A atividade é aberto no designer de fluxo de trabalho.

3.  No Designer de fluxo de trabalho, clique o **argumentos** guia.

4.  Clique em **criar argumento**. Nomeie o novo argumento **itens**.

5.  No **tipo de argumento** coluna, selecione **matriz de T []**.

6.  No navegador de tipo, selecione **objeto** e, em seguida, selecione **Okey**.

7.  Clique em **criar argumento** novamente. Nomeie o novo argumento **corpo**. No **direção** coluna para o novo argumento, selecione **propriedade**.

8.  Na coluna de tipo de argumento, selecione **procurar tipos**

9. No navegador de tipo, insira **ActivityAction** na **nome do tipo** campo. Selecione **ActivityAction\<T >** na exibição de árvore. Selecione **objeto** na lista suspensa que aparece para atribuir o tipo **ActivityAction\<objeto >** ao argumento.

10. Arraste um <xref:System.Activities.Statements.While> atividade a partir de **fluxo de controle** seção da caixa de ferramentas para a superfície do designer.

11. Selecione o <xref:System.Activities.Statements.While> atividade e selecione o **variáveis** guia.

12. Selecione **criar variável**. Nomeie a nova variável **índice**.

13. No **tipo de variável** coluna, selecione **Int32**. Deixe o **escopo** como **enquanto**e o **padrão** coluna em branco.

14. Definir a **condição** propriedade do <xref:System.Activities.Statements.While> atividade **índice < Items.Length;**.

15. Arraste um <xref:System.Activities.Statements.InvokeDelegate> a atividade do **primitivos** seção da caixa de ferramentas para o **corpo** do <xref:System.Activities.Statements.While> atividade.

16. Selecione **corpo** no menu suspenso do delegado.

17. No **propriedades** grade para o <xref:System.Activities.Statements.InvokeDelegate> atividade, clique no **...**  botão de **argumentos do delegado** propriedade.

18. No **valor** coluna de argumento nomeado **argumento**, insira **itens [Index]**. Clique em **Okey** para fechar o **DelegateArguments** caixa de diálogo.

19. Arraste uma atividade de <xref:System.Activities.Statements.Assign> na linha horizontal abaixo de atividade de <xref:System.Activities.Statements.InvokeDelegate> . O <xref:System.Activities.Statements.Assign> atividade é criada e uma <xref:System.Activities.Statements.Sequence> atividade é criada automaticamente para conter as duas atividades na **corpo** seção o **MyForEach** atividade. A sequência é necessária, pois o **corpo** seção pode conter apenas uma única atividade. Criar automaticamente uma nova <xref:System.Activities.Statements.Sequence> atividade é um novo recurso do .NET Framework 4.5.

20. Definir a **para** propriedade do <xref:System.Activities.Statements.Assign> atividade **índice**. Definir a **valor** propriedade da **atribuir** atividade para **index+1**.

   Personalizado **MyForEach** atividade invoca uma atividade arbitrária uma vez para cada valor passado nele através de **itens** coleção, com os valores na coleção como entradas para a atividade.

## <a name="use-the-custom-activity-in-a-workflow"></a>Use a atividade personalizado em um fluxo de trabalho

1.  Compile o projeto pressionando **Ctrl**+**Shift**+**B**.

2.  Na **Gerenciador de soluções**, abra **Workflow1.xaml** no designer.

3.  Arraste uma **MyForEach** atividade da caixa de ferramentas para a superfície do designer. A atividade está em uma seção da caixa de ferramentas com o mesmo nome que o projeto.

4.  Defina a **itens** propriedade da **MyForEach** atividade para **novo objeto [] {1, "abc"}**.

5.  Arraste uma <xref:System.Activities.Statements.WriteLine> a atividade do **primitivos** seção da caixa de ferramentas a **Delegate: corpo** seção o **MyForEach** atividade.

6.  Definir a **texto** propriedade da <xref:System.Activities.Statements.WriteLine> atividade **argument**.

Quando o fluxo de trabalho é executado, o console mostra a saída a seguir:

**1**
**abc**