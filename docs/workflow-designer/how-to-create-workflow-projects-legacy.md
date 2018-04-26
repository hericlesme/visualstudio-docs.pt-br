---
title: 'Designer de fluxo de trabalho - como: criar projetos de fluxo de trabalho (legados)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb5d58c6d450a5e68d804e33785ec76349bfb6d8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>Como: Criar projetos de fluxo de trabalho (o legados)

Siga estas etapas para criar um projeto do Windows Workflow Foundation (WF) que tem como alvo o .NET Framework versão 3.5 ou o WinFX. Este procedimento usa o Designer de fluxo de trabalho herdado do Windows fornecidas pelo Visual Studio 2010.

## <a name="to-create-a-workflow-project"></a>Para criar um projeto de fluxo de trabalho

1.  Inicie o Visual Studio.

2.  No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3.  Selecione o **.NET Framework 3.0** opção ou **.NET Framework 3.5** opção no menu suspenso na parte superior da lista da **novo projeto** janela para acessar o designer herdado.

    > [!NOTE]
    > A opção padrão no Visual Studio 2010 é **.NET Framework 4**. Essa opção é usada para criar aplicativos do Windows Workflow Foundation (WF) que visam o .NET Framework 4 e não usar o designer herdado.

4.  No **tipos de projeto** painel, selecione os projetos do Visual c# ou Visual Basic e, em seguida, selecione **fluxo de trabalho**.

5.  No **modelos** painel, selecione um dos modelos de projeto instalado:

    -   Aplicativo de console sequencial de fluxo de trabalho

    -   Sequencial biblioteca de fluxo de trabalho

    -   Biblioteca de atividade de fluxo de trabalho

    -   Aplicativo de console do fluxo de trabalho do computador de estado

    -   Biblioteca de fluxo de trabalho do computador de estado

    -   Fluxo de trabalho vazio Projeto

6.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.

7.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até o diretório.

     Se você desejar um diretório da solução para o projeto, selecione o **criar diretório para solução** caixa de seleção e insira um nome no **nome da solução** caixa.

8.  Clique em **OK**.

## <a name="see-also"></a>Consulte também

- [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)