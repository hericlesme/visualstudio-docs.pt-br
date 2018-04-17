---
title: Na visão geral de documentos do Office, os controles dos Windows Forms | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2693c31d06edc621f355749f76caf04e44fb28e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Visão geral de controles dos Windows Forms em documentos do Office
  Controles de formulários do Windows são objetos que os usuários podem interagir com a inserção ou manipular dados. Em projetos de nível de documento para o Microsoft Office Excel e o Microsoft Office Word, você pode adicionar controles de formulários do Windows para o documento ou a pasta de trabalho em seu projeto em tempo de design ou você pode adicionar programaticamente desses controles em tempo de execução. Você pode programaticamente adicionar esses controles para qualquer documento aberto ou planilha em tempo de execução em um suplemento do VSTO para Excel ou Word.  
  
 Para obter mais informações, consulte [como: adicionar controles dos Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="using-windows-forms-controls"></a>Usando o Windows Forms a controles  
 Você pode adicionar controles de Windows Forms a documentos e elementos de interface do usuário do usuário personalizável, incluindo painéis de ações, painéis de tarefas personalizados e formulários do Windows. Controles de formulários do Windows geralmente têm o mesmo comportamento em documentos como os outros elementos de interface do usuário, mas existem algumas diferenças. Para obter informações, consulte [limitações de controles dos Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 A decisão se deseja adicionar controles de formulários do Windows para um documento ou algum outro elemento de interface do usuário depende de vários fatores. Ao projetar a interface do usuário de sua solução, considere os usos dos controles de formulários do Windows conforme descrito na tabela a seguir.  
  
 Em um documento.  
 -   Quando você deseja exibir os controles de 100% do tempo.  
  
-   Quando você quiser que os usuários insiram dados diretamente no documento, por exemplo, em documentos com base em formulários em que a superfície de edição está bloqueado.  
  
-   Quando você deseja que os controles para exibir em linha com os dados no documento. Por exemplo, se você estiver adicionando botões para cada linha de um objeto de lista, você desejaria-los em linha com cada item de lista.  
  
 No painel de ações ou um painel tarefa personalizada.  
 -   Quando você deseja fornecer informações contextuais ao usuário.  
  
-   Quando você quiser apenas os resultados sejam exibidos no documento e não a controles de consulta e dados.  
  
-   Quando você deseja garantir que os controles não são impressos com o documento.  
  
-   Quando você deseja garantir que os controles não interferir ao modo de exibição do documento.  
  
 Em um Windows Form.  
 -   Quando você quiser controlar o tamanho da interface do usuário.  
  
-   Quando você quiser impedir que os usuários ocultem ou excluir os controles.  
  
-   Quando você deseja obter entrada do usuário e impedir que o usuário fazer qualquer coisa no documento até que a entrada seja recebida.  
  
## <a name="adding-windows-forms-controls-programmatically"></a>Adicionando controles dos Windows Forms programaticamente  
 Você pode adicionar controles de Windows Forms a documentos do Word e planilhas do Excel em tempo de execução. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fornece métodos auxiliares para adicionar os controles de Windows Forms mais comuns. Esses métodos auxiliares permitem adicionar rapidamente controles para o seu documento do Office e o acesso a funcionalidade de controle de Windows Forms combinada e funcionalidades relacionados ao Office desses controles.  
  
 Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="using-windows-forms-controls-in-document-level-projects"></a>Usando o Windows Forms controles em nível de documento  
 Alguns aspectos do uso de controles de Windows Forms em documentos são exclusivos a projetos no nível de documento, que permitem que você criar a interface do usuário do seu documento usando o designer do Visual Studio.  
  
### <a name="creating-custom-user-controls"></a>Criando controles de usuário personalizada  
 Você pode adicionar um controle de usuário ao seu projeto e, em seguida, adicioná-lo para o **caixa de ferramentas**. Em seguida, você pode arrastar o controle de usuário diretamente para o documento da mesma maneira que você adicionaria um controle de formulários do Windows para o documento. Há algumas coisas para ter em mente ao criar controles de usuário:  
  
-   Não crie um **lacrado** controle de usuário. Quando você arrasta o controle para o documento, o Visual Studio gera uma classe wrapper derivada do controle de usuário para estendê-lo e suporte para seu uso no documento. Se o controle de usuário é **lacrado**, Visual Studio não é possível gerar a classe de invólucro.  
  
-   Controles de usuário devem ter o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo definido como **true**. Controles de usuário criados dentro de um projeto do Office tem este atributo definido como **true** por padrão, mas o usuário controles que fazem parte de projetos externos talvez não tenha esse atributo definido como **true**.  
  
-   Depois de adicionar um controle de usuário para o documento, não renomeie ou exclua o <xref:System.Windows.Forms.UserControl> classe do projeto. Se você precisar alterar o nome de um controle de usuário, você deve primeiro excluí-lo do documento e, em seguida, adicioná-lo novamente depois que o nome foi alterado.  
  
### <a name="arranging-controls-at-design-time"></a>Organizando controles em tempo de Design  
 Se você adicionar vários controles a documentos do Word e Excel no tempo de design, você pode definir o alinhamento de todos os controles selecionados rapidamente usando o **Microsoft Office Word** e **do Microsoft Office Excel**barras de ferramentas no Visual Studio. Essas barras de ferramentas estão disponíveis somente quando um documento ou a planilha é aberta no designer.  
  
 Quando você seleciona vários controles no designer, você pode usar os botões a seguir nessas barras de ferramentas para organizar os controles:  
  
-   **Alinhar à esquerda**  
  
-   **Alinhar centros**  
  
-   **Alinhar os direitos**  
  
-   **Alinhar as partes superiores**  
  
-   **Alinhar meios**  
  
-   **Alinhar a parte inferior**  
  
-   **Igualar espaçamento Horizontal**  
  
-   **Igualar espaçamento Vertical**  
  
> [!NOTE]  
>  Em projetos do Word, esses botões são ativados somente se os controles selecionados não estão alinhados com o texto. Por padrão, os controles que você adicionar ao documento em tempo de design estejam de acordo com o texto.  
  
### <a name="preventing-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Impedindo que os dados antigos que aparecem em pastas de trabalho do Excel durante o carregamento  
 Quando você adicionar controles de Windows Forms em documentos ou planilhas em tempo de design, os controles permanecem no documento quando o usuário fecha o documento. Também são chamados de controles adicionados em tempo de design *controles estáticos*.  
  
 Quando uma pasta de trabalho do Excel que contém os controles estáticos é aberta, a pasta de trabalho exibe um bitmap do controle em um controle ActiveX, até que o código de personalização é executado e o controle real é carregado. O Excel cria esse bitmap e armazena-o na pasta de trabalho sempre que a pasta de trabalho é salvo. O bitmap mostra o controle como apareceu na última vez em que a pasta de trabalho foi salvo, incluindo quaisquer dados que o controle foi exibindo. Para obter mais informações sobre o controle ActiveX que contém os controles de formulários do Windows e bitmaps, consulte [limitações de controles dos Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Em determinadas condições, o código não carrega e somente o bitmap é exibido, como quando o usuário abre a pasta de trabalho no modo de design. Além disso, se o usuário abre a pasta de trabalho em um computador que não tenha o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instalado, a personalização não pode ser executado para carregar os controles e, portanto, somente o bitmap do controle está visível. Você sempre deve remover informações pessoais dos controles em pastas de trabalho antes de salvar a pasta de trabalho e enviá-la a outro usuário para garantir que suas informações pessoais não são passadas acidentalmente.  
  
### <a name="matching-control-size-to-cell-size-on-an-excel-worksheet"></a>Correspondência de tamanho de controle para a célula de tamanho em uma planilha do Excel  
 Você pode definir o controle a ser redimensionado automaticamente quando o tamanho da célula pai for alterado. Para obter mais informações, consulte [como: redimensionar controles em células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Adicionando componentes que são compartilhados por todas as planilhas  
 Você pode adicionar os componentes que você deseja compartilhar entre todas as planilhas, como um <xref:System.Data.DataSet>, para o Designer de pasta de trabalho em vez de para planilhas. O componente será exibido na bandeja do componente.  
  
### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Fórmula para inserir controles em uma planilha do Excel  
 Quando você seleciona um controle no Excel, você verá **=EMBED("WinForms.Control.Host","")** no **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.  
  
### <a name="layout-style-of-controls-on-a-word-document"></a>Estilo de layout de controles em um documento do Word  
 Quando você adicionar um controle para o documento do Word em um projeto no nível de documento usando o designer do Visual Studio, o controle é adicionado em linha com o texto. Para alterar o estilo de layout do controle, clique com botão direito no controle e, em seguida, clique em **Formatar controle**. Selecione uma disposição no **Layout** página do **Formatar objeto** caixa de diálogo.  
  
 Quando você adiciona um controle a um documento do Word em tempo de execução, você pode especificar o estilo de layout do novo controle usando diferentes `Add` \< *classe de controle*> sobrecargas de método do <xref:Microsoft.Office.Tools.Word.ControlCollection> classe:  
  
-   Para adicionar o controle de acordo com o texto, use uma sobrecarga que aceita um <xref:Microsoft.Office.Interop.Word.Range> que especifica o local do controle.  
  
-   Para adicionar o controle como uma forma flutuante, use uma sobrecarga que aceita as coordenadas esquerdas e superior do controle.  
  
 Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Se você abrir um modelo do Word no Visual Studio designer, controles não embutido no modelo podem não estar visíveis porque o Visual Studio abrirá o modelo no **Normal** exibição. Para exibir os controles, altere o modo de exibição **Layout de impressão**.  
  
### <a name="controls-outside-the-main-document-body"></a>Controles fora do corpo do documento principal  
 Controles de formulários do Windows não têm suporte dentro de um cabeçalho ou rodapé, ou em um subdocumento.  
  
### <a name="adding-components-at-design-time"></a>Adicionando componentes em tempo de Design  
 Determinados controles ou componentes não são visíveis no documento e em vez disso, são exibidos em uma bandeja de componente. Visual Studio fornece uma bandeja de componentes para cada janela de documento. Bandeja de componentes na tela só aparecerá se componentes existir no documento.  
  
## <a name="see-also"></a>Consulte também  
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Visão geral do painel de ações](../vsto/actions-pane-overview.md)   
 [Controles dos Windows Forms](/dotnet/framework/winforms/controls/index)   
 [Limitações de controles dos Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Como: adicionar controles a documentos do Office do Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Como: redimensionar controles dentro das células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Como: ocultar controles em planilhas durante a impressão](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Passo a passo: Alterando a formatação da planilha usando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Passo a passo: Alterando a formatação do documento usando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [Passo a passo: Exibindo texto em uma caixa de texto em uma planilha usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Passo a passo: Exibindo texto em uma caixa de texto em um documento usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Limitações de controles dos Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Passo a passo: Atualizando um gráfico em um documento usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [Instruções passo a passo: atualizando um gráfico em uma planilha usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  