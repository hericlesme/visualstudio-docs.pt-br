---
title: 'Como: criar uma biblioteca de atividades | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 151e3f84636273de253937ebf5c91cff066b9f85
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-an-activity-library"></a>Como: Crie uma biblioteca de atividade
As atividades personalizados são usadas para modelar seus processos comerciais específicos em um fluxo de trabalho. O modelo de biblioteca de atividades no [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] foi fornecido para permitir a criação de tais atividades personalizadas visualmente usando o Designer de fluxo de trabalho do Windows.

### <a name="to-create-a-workflow-activity-library"></a>Para criar uma biblioteca de atividade de fluxo de trabalho

1.  Inicie o [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, selecione **projeto...** .

     A caixa de diálogo **Novo Projeto** é aberta.

3.  No **tipos de projeto** painel, selecione **fluxo de trabalho** do **Visual C#** projetos ou **Visual Basic** agrupamentos dependendo de sua preferência de idioma.

4.  No **modelos** painel, selecione **biblioteca de atividades**.

5.  No **nome** caixa, digite um nome descritivo para o seu projeto para tornar mais fácil de identificar.

6.  No **local** caixa, digite no diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

7.  No **solução** caixa, digite um nome descritivo para sua solução e clique em **Okey**.

    > [!NOTE]
    > Se você quiser adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra essa solução no [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], clique com botão direito da solução de **Solution Explorer**e selecione **adicionar**, em seguida,  **Novo projeto...**  para abrir o **novo projeto** caixa de diálogo. Continuar conforme descrito acima neste procedimento.

8.  O modelo de projeto cria uma definição de atividade em XAML. Designer de fluxo de trabalho do Windows é aberto e exibe a tela para a atividade personalizada.

9. Arraste uma atividade a partir de **caixa de ferramentas** para a superfície de design para incluí-lo em sua atividade personalizada.

    > [!CAUTION]
    > Uma atividade é permitida você só filho no corpo da atividade personalizado; no entanto, a atividade filho pode ser uma atividade de composição, como uma atividade de <xref:System.Activities.Statements.Sequence> ou a atividade de <xref:System.Activities.Statements.Flowchart> .

## <a name="see-also"></a>Consulte também

- [Como criar uma atividade](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)