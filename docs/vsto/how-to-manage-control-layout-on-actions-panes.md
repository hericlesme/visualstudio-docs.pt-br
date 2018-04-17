---
title: 'Como: gerenciar o controle Layout em painéis de ações | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0831740c612e4e9d4eddd47a0648302e9460f060
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Como gerenciar o layout de controle em painéis de ações
  Um painel de ações está encaixado à direita de um documento ou planilha por padrão. No entanto, pode ser encaixado à esquerda, superior ou inferior. Se você estiver usando vários controles de usuário, você pode escrever código para pilha corretamente os controles de usuário no painel Ações. Para obter mais informações, consulte [visão geral do painel de ações](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 A ordem de pilha dos controles depende se o painel de ações está encaixado verticalmente ou horizontalmente.  
  
> [!NOTE]  
>  Se o usuário redimensionar o painel de ações em tempo de execução, você pode definir os controles para redimensionar com o painel de ações. Você pode usar o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade de um controle de formulários do Windows para controles de âncora para o painel de ações. Para obter mais informações, consulte [como: âncora controles nos Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Para definir a ordem de pilha dos controles do painel de ações  
  
1.  Abra um projeto no nível do documento para o Microsoft Office Word que inclui um painel de ações com vários controles de usuário ou controles do painel de ações aninhada. Para obter mais informações, consulte [como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Clique com botão direito **ThisDocument.cs** ou **ThisDocument. vb** na **Solution Explorer** e, em seguida, clique em **Exibir código**.  
  
3.  No <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> manipulador de eventos do painel de ações, verifique se a orientação do painel de ações é horizontal.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  Se a orientação horizontal, empilhar os controles do painel de ação da esquerda; Caso contrário, a pilha-los da parte superior.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  Em c#, você deve adicionar um manipulador de eventos para o `ActionsPane` para o <xref:Microsoft.Office.Tools.Word.Document.Startup> manipulador de eventos. Para obter informações sobre como criar manipuladores de eventos, consulte [como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Execute o projeto e verifique se os controles do painel de ações são empilhados esquerda para a direita quando o painel de ações está encaixado na parte superior do documento, e os controles são empilhados de cima para baixo quando o painel de ações está encaixado à direita do documento.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um projeto de nível de documento do Word com um painel de ações que contém vários controles de usuário ou ações aninhada controla.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do painel de ações](../vsto/actions-pane-overview.md)   
 [Como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Passo a passo: Inserindo texto em um documento de um painel de ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Instruções passo a passo: inserindo texto em um documento de um painel Ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  