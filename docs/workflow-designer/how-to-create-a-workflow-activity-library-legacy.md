---
title: 'Designer de fluxo de trabalho - como: criar uma biblioteca de atividades de fluxo de trabalho (legados)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 432766e60ee1384db0f8cd5bad1f369e80ddd20a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973161"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Como: Crie uma biblioteca de atividade de fluxo de trabalho (o legados)

Siga estas etapas para criar um projeto de biblioteca de atividades de fluxo de trabalho usando herdado Designer de fluxo de trabalho do Windows fornecido pelo Visual Studio 2010. Use o Designer de fluxo de trabalho herdado quando você precisa direcionar o .NET Framework versão 3.5 ou o WinFX.

## <a name="to-create-a-workflow-activity-library-project"></a>Para criar um projeto de biblioteca de atividade de fluxo de trabalho

1.  Inicie o Visual Studio.

2.  No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3.  Selecione o **.NET Framework 3.0** opção ou **.NET Framework 3.5** opção no menu suspenso na parte superior da lista da **novo projeto** janela para acessar o designer herdado.

    > [!NOTE]
    > A opção padrão no Visual Studio 2010 é **.NET Framework 4**. Essa opção é usada para criar aplicativos do Windows Workflow Foundation (WF) que visam o .NET Framework 4 e não usar o designer herdado.

4.  No **tipos de projeto** painel, selecione Visual c# ou Visual Basic (em **outras linguagens**) e, em seguida, selecione **fluxo de trabalho**.

5.  No **modelos** painel, selecione **biblioteca de atividades de fluxo de trabalho**.

6.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.

7.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

     Se você desejar um diretório da solução para o projeto, selecione o **criar diretório para solução** caixa de seleção e insira um nome no **nome da solução** caixa.

8.  Clique em **OK**.

## <a name="see-also"></a>Consulte também

- [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)
- [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)
- [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)
- [Desenvolvimento de atividades de fluxo de trabalho](http://msdn.microsoft.com/en-us/19876dfc-dfa5-4d52-b1f5-1d087474cc52)
- [Atividades do Windows Workflow Foundation](http://msdn.microsoft.com/en-us/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)