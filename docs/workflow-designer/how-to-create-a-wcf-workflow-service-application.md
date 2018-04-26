---
title: 'Designer de fluxo de trabalho - como: criar um aplicativo de serviço de fluxo de trabalho WCF'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93fb69862c228a3b6e61467facba188dd20c67c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Como: Crie um aplicativo de Serviço WCF de Fluxo de Trabalho

Aplicativos de serviço de fluxo de trabalho do Windows Communication Foundation (WCF) são serviços de comunicações distribuído que passam mensagens entre clientes e a mesmos limites de processo. A implementação do contrato de serviço no lado do serviço é feita declarativamente por meio de atividades de fluxo de trabalho no .NET Framework 4, de modo semelhante aos serviços de fluxo de trabalho herdados no .NET Framework 3.5.

## <a name="to-create-a-wcf-workflow-service-application"></a>Para criar um aplicativo de serviço do fluxo de trabalho WCF

1.  Inicie o Visual Studio 2010.

2.  No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3.  No **modelos instalados** painel, selecione **WCF** ou **fluxo de trabalho** do **Visual C#** ou **doVisualBasic** agrupamentos dependendo de você idioma de preferência.

4.  No painel central, selecione **aplicativo de serviço de fluxo de trabalho WCF**.

5.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.

6.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

7.  No **solução** , selecione para criar uma nova solução e, em seguida, clique em **Okey**.

    > [!NOTE]
    > Se você quiser adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra a solução no Visual Studio 2010, clique com botão direito a solução em **Solution Explorer**e selecione **adicionar**, em seguida,  **Novo projeto** para abrir o **novo projeto** caixa de diálogo. Continuar conforme descrito acima neste procedimento.

8.  O modelo de projeto cria uma definição de serviço como XAML. Abre o Designer de fluxo de trabalho do Windows para o modo de design com uma <xref:System.Activities.Statements.Sequence> atividade que contém um conjunto de <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> atividades.

## <a name="see-also"></a>Consulte também

- [Como criar uma atividade](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)