---
title: 'Passo a passo: Programando em eventos de um controle NamedRange | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: "57"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40076f607e66ec76aaa42ae297d22b38a6234ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-programming-against-events-of-a-namedrange-control"></a>Instruções passo a passo: programando em eventos de um controle NamedRange
  Este passo a passo demonstra como adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle a uma planilha do Microsoft Office Excel e o programa em relação a seus eventos usando ferramentas de desenvolvimento do Office no Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este passo a passo, você aprenderá a:  
  
-   Adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle em uma planilha.  
  
-   Programar <xref:Microsoft.Office.Tools.Excel.NamedRange> eventos de controle.  
  
-   Seu projeto de teste.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 Nesta etapa, você criará um projeto de pasta de trabalho do Excel usando o Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Para criar um novo projeto  
  
1.  Criar um projeto de pasta de trabalho do Excel com o nome **Meus eventos de intervalo nomeado**. Verifique se **criar um novo documento** está selecionado. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre a nova pasta de trabalho do Excel no designer e adiciona o **Meus eventos de intervalo nomeado** projeto **Gerenciador de soluções**.  
  
## <a name="adding-text-and-named-ranges-to-the-worksheet"></a>Adicionando texto e intervalos nomeados para a planilha  
 Porque os controles de host são estendidos de objetos do Office, você pode adicioná-los ao documento da mesma maneira, você adicionaria o objeto nativo. Por exemplo, você pode adicionar uma Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> controle em uma planilha, abrindo o **inserir** menu, apontando para **nome**e escolhendo **definir**. Você também pode adicionar uma <xref:Microsoft.Office.Tools.Excel.NamedRange> controle arrastando-o do **caixa de ferramentas** para a planilha.  
  
 Nesta etapa, você adicionará dois controles de intervalo nomeado para a planilha usando o **caixa de ferramentas**e, em seguida, adicionar texto à planilha.  
  
#### <a name="to-add-a-range-to-your-worksheet"></a>Para adicionar um intervalo à sua planilha  
  
1.  Verifique o **Meus Events.xlsx de intervalo nomeado** pasta de trabalho é aberta no designer do Visual Studio, com `Sheet1` exibida.  
  
2.  Do **Excel controles** guia da caixa de ferramentas, arraste um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle a célula **A1** em `Sheet1`.  
  
     O **adicionar NamedRange controle** caixa de diálogo é exibida.  
  
3.  Verifique **$A$ 1** aparece na caixa de texto editável e que a célula **A1** está selecionado. Se não estiver, clique na célula **A1** para selecioná-la.  
  
4.  Clique em **OK**.  
  
     Célula **A1** torna-se um intervalo nomeado `namedRange1`. Não há nenhuma indicação visível na planilha, mas `namedRange1` aparece no **nome** caixa (localizada imediatamente acima da planilha no lado esquerdo) quando a célula **A1** está selecionado.  
  
5.  Adicione outro <xref:Microsoft.Office.Tools.Excel.NamedRange> controle a célula **B3**.  
  
6.  Verifique **$B$ 3** aparece na caixa de texto editável e que a célula **B3** está selecionado. Se não estiver, clique na célula **B3** para selecioná-la.  
  
7.  Clique em **OK**.  
  
     Célula **B3** torna-se um intervalo nomeado `namedRange2`.  
  
#### <a name="to-add-text-to-your-worksheet"></a>Para adicionar texto à sua planilha  
  
1.  Na célula **A1**, digite o seguinte texto:  
  
     **Este é um exemplo de um controle NamedRange.**  
  
2.  Na célula **A3** (à esquerda do `namedRange2`), digite o seguinte texto:  
  
     **Eventos:**  
  
 As seções a seguir, você irá escrever código que insere o texto no `namedRange2` e modifica as propriedades do `namedRange2` controle em resposta ao <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, e <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> eventos de `namedRange1`.  
  
## <a name="adding-code-to-respond-to-the-beforedoubleclick-event"></a>Adicionando código para responder ao evento BeforeDoubleClick  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Para inserir texto no NamedRange2 com base no evento BeforeDoubleClick  
  
1.  Em **Solution Explorer**, clique com botão direito **Sheet1.vb** ou **Sheet1.cs** e selecione **Exibir código**.  
  
2.  Adicione código para que o `namedRange1_BeforeDoubleClick` manipulador de eventos é semelhante ao seguinte:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  Em c#, você deve adicionar manipuladores de eventos para o intervalo nomeado conforme o <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento abaixo. Para obter informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="adding-code-to-respond-to-the-change-event"></a>Adicionando código para responder ao evento de alteração  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Para inserir texto no namedRange2 com base no evento de alteração  
  
1.  Adicione código para que o `NamedRange1_Change` manipulador de eventos é semelhante ao seguinte:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Porque clicando duas vezes em uma célula em um intervalo do Excel entra em modo de edição, um <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> evento ocorre quando a seleção é movida fora do intervalo, mesmo que nenhuma alteração ao texto ocorreu.  
  
## <a name="adding-code-to-respond-to-the-selectionchange-event"></a>Adicionando código para responder ao evento SelectionChange  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Para inserir texto no namedRange2 com base no evento SelectionChange  
  
1.  Adicione código para que o **NamedRange1_SelectionChange** manipulador de eventos é semelhante ao seguinte:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Porque clicando duas vezes em uma célula em um intervalo do Excel faz com que a seleção será movida para o intervalo, um <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> evento ocorre antes do <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> evento ocorre.  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora você pode testar sua pasta de trabalho para verificar que o texto que descreve os eventos de um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é inserido em outro intervalo nomeado quando os eventos são gerados.  
  
#### <a name="to-test-your-document"></a>Para testar o documento  
  
1.  Pressione F5 para executar o projeto.  
  
2.  Coloque o cursor no `namedRange1`e verificar se o texto em relação a <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> eventos é inserido e um comentário é inserido na planilha.  
  
3.  Clique duas vezes em `namedRange1`e verificar se o texto sobre <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> eventos é inserido com texto em itálico vermelho no `namedRange2`.  
  
4.  Clique fora do `namedRange1` e observe que o evento de alteração ocorre quando sair do modo de edição, mesmo que nenhuma alteração para o texto foi feita.  
  
5.  Alterar o texto em `namedRange1`.  
  
6.  Clique fora do `namedRange1`e verificar se o texto sobre <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> eventos é inserido com texto azul em `namedRange2`.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo mostra as Noções básicas de programação em eventos de um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle. Aqui está uma tarefa que pode vir a seguinte:  
  
-   Implantar o projeto. Para obter mais informações, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Como: redimensionar controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Como criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  