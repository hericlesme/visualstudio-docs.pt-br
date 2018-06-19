---
title: 'Designer de fluxo de trabalho - como: criar aplicativos de Console de fluxo de trabalho de máquina de estado (o legados)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 805b048a9e30f7a637e178d223b962259dadd926
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971343"
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Como: Criar aplicativos de console do fluxo de trabalho do computador de estado (o legados)

Siga estas etapas para criar um projeto de aplicativo de Console de fluxo de trabalho de máquina de estado usando herdado Designer de fluxo de trabalho do Windows fornecido pelo Visual Studio 2010. Use o Designer de fluxo de trabalho herdado quando você precisa direcionar o .NET Framework versão 3.5 ou o WinFX.

## <a name="to-create-a-state-machine-application-project"></a>Para criar um projeto de aplicativo do computador de estado

1.  Inicie o Visual Studio.

2.  No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3.  Selecione o **.NET Framework 3.0** opção ou **.NET Framework 3.5** opção no menu suspenso na parte superior da lista da **novo projeto** janela para acessar o designer herdado.

    > [!NOTE]
    > A opção padrão no Visual Studio 2010 é **.NET Framework 4**. Essa opção é usada para criar aplicativos do Windows Workflow Foundation (WF) que visam o .NET Framework 4 e não usar o designer herdado.

4.  No **tipos de projeto** painel, selecione Visual c# ou Visual Basic (em **outras linguagens**) e, em seguida, selecione **fluxo de trabalho**.

5.  No **modelos** painel, selecione **aplicativo de Console de fluxo de trabalho de máquina de estado**.

6.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.

7.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

     Se você desejar um diretório da solução para o projeto, selecione o **criar diretório para solução** caixa de seleção e insira um nome no **nome da solução** caixa.

8.  Clique em **OK**.

## <a name="see-also"></a>Consulte também

- [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)
- [Como criar uma biblioteca de fluxo de trabalho da máquina de estado (herdado)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)