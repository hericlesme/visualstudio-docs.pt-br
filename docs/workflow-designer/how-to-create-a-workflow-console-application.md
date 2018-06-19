---
title: 'Designer de fluxo de trabalho - como: criar um aplicativo de Console do fluxo de trabalho'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970894"
---
# <a name="how-to-create-a-workflow-console-application"></a>Como: Crie um aplicativo de console do fluxo de trabalho

Windows Workflow Foundation (WF) permite que você crie fluxos de trabalho para executar processos humanos ou sistema. O Designer de fluxo de trabalho do Windows fornece a superfície de design para criar esses fluxos de trabalho. O Designer de fluxo de trabalho pode ser usado para criar fluxos de trabalho do Visual Studio ou ele pode ser integrado a outros aplicativos que o novo host do designer.

Este tópico descreve como usar o Designer de fluxo de trabalho no Visual Studio 2010 para criar um fluxo de trabalho em um aplicativo de console.

## <a name="to-create-a-workflow-console-application"></a>Para criar um aplicativo de console do fluxo de trabalho

1.  Inicie o Visual Studio 2010.

2.  No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3.  No **modelos instalados** painel, selecione **fluxo de trabalho** do **Visual C#** ou **Visual Basic** agrupamentos, dependendo de sua idioma de preferência.

4.  No painel central, selecione **aplicativo de Console do fluxo de trabalho**.

5.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.

6.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

7.  No **solução** , digite o nome para a nova solução. Clique em **Okey** para criar o aplicativo.

    > [!NOTE]
    > Se você quiser adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra a solução no Visual Studio 2010, clique com botão direito a solução em **Solution Explorer**e selecione **adicionar**, em seguida,  **Novo projeto** para abrir o **novo projeto** caixa de diálogo. Continuar conforme descrito acima neste procedimento.

8.  O modelo de projeto cria uma definição de fluxo de trabalho em XAML e a definição de aplicativo de console está no código-fonte. O Designer de fluxo de trabalho é aberta e exibe a tela do fluxo de trabalho que você criou.

9. Para criar um fluxo de trabalho, arraste atividades ou outros itens de fluxo de trabalho do **caixa de ferramentas** à superfície de design do fluxo de trabalho.

## <a name="see-also"></a>Consulte também

- [Criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)