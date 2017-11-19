---
title: "Limitações do Windows Forms a controles em documentos do Office | Microsoft Docs"
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f8842bd80832211f02532ca706416416325663b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitações de controles dos Windows Forms em documentos do Office
  Há algumas diferenças entre os controles de formulários do Windows que são adicionados a documentos do Microsoft Office Word ou planilhas do Excel do Microsoft Office e controles de formulários do Windows que são adicionados ao Windows Forms. Por exemplo, quando você adiciona um <xref:Microsoft.Office.Tools.Word.Controls.Button> controlar como um documento, propriedades <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A>, e <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> não se comportar como esperado.  
  
 Muitas dessas diferenças são causadas pela maneira que os controles são hospedados do Windows Forms em documentos. Quando um controle de formulários do Windows é adicionado a um documento, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incorpora um controle ActiveX que hospeda, em seguida, o controle de formulários do Windows no documento. O controle de formulários do Windows não é inserido diretamente no documento.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitações de métodos e propriedades de controles de formulários do Windows  
 Há vários métodos e propriedades de controles de formulários do Windows que não funcionam da mesma forma em um documento como fariam em um formulário do Windows e, portanto, é recomendável que elas não usada. Por exemplo, definir propriedades como `Dock` e `Anchor` só afeta a posição do controle em relação à caixa de controles ActiveX, em vez do documento. A seguir está uma lista de métodos sem suporte e as propriedades de controles de formulários do Windows para o Word e Excel:  
  
-   Não há suporte para métodos e propriedades de controles do Excel:  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Não há suporte para métodos e propriedades de controles do Word:  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Você também não é possível definir o `Left` ou `Top` propriedade de controles de formulários do Windows que estejam de acordo com o texto em um documento do Word. Controles de formulários do Windows são adicionados em linha com o texto nos seguintes casos:  
  
-   Programaticamente, você adiciona um controle a um documento do Word e usa um método que especifica um intervalo para o local.  
  
-   Você pode adicionar um controle de formulários do Windows para um documento do Word em tempo de design. Você pode alterar isso, modificando o controle no designer.  
  
## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Diferenças em controles dos Windows Forms em documentos do Office  
 Controles de formulários do Windows geralmente têm o mesmo comportamento em um documento do Office como eles em um formulário do Windows, mas existem algumas diferenças. A tabela a seguir descreve as diferenças que existem para controles de Windows Forms em documentos do Office.  
  
|Funcionalidade|Diferença|  
|-------------------|----------------|  
|Ordem de tabulação do controle|Não é possível percorrer controles colocados em uma planilha do Excel ou um documento do Word.|  
|Agrupamento de controle|Não é possível usar um <xref:System.Windows.Forms.GroupBox> controle para conter outros controles em um documento do Office. Quando você adiciona vários botões de opção diretamente para o documento, os botões de opção não são mutuamente exclusivos. Você pode escrever código para tornar os botões de opção mutuamente exclusivos; No entanto, a abordagem preferencial é adicionar os botões de opção para um controle de usuário e, em seguida, adicione o controle de usuário para o documento. Para obter mais informações, consulte o exemplo de controles de Word ou Excel controles de amostra em [amostras de desenvolvimento do Office e explicações passo a passo](../vsto/office-development-samples-and-walkthroughs.md).|  
|Tipo de controle|Controles de formulários do Windows usados em documentos são encapsulados em uma classe fornecida pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que fornece funcionalidade adicional específica os controles para a planilha do Excel ou um documento do Word. Por exemplo, se você tiver um `Button` control em uma planilha do Excel, certifique-se de especificar o tipo como <xref:Microsoft.Office.Tools.Excel.Controls.Button> em vez de <xref:System.Windows.Forms.Button> quando a referência ou a conversão do objeto.|  
|Tamanho e posição de controle|O tamanho e a posição do controle é determinada pelas propriedades que fazem parte do contêiner de controle ActiveX. As propriedades do controle ActiveX ter valores diferentes que as propriedades equivalentes de um controle de formulários do Windows. Quando você define o `Top`, `Left`, `Height`, ou `Width` propriedades de um controle, ele é medido em pontos, em vez de pixels.|  
|Posição do controle em documentos do Word|Se você adicionar controles a um layout de fluxo, tenha em mente que os controles fluirá com o conteúdo como as alterações de conteúdo. Você não pode ancorar o controle a um parágrafo quando você arrasta-o do **caixa de ferramentas** porque o controle é adicionado ao documento do Word em linha com o texto. Se você usar outro método para adicionar o controle, como duas vezes no controle, o controle é inserido acordo com a opção de palavra que você definiu para a inserção de imagens.<br /><br /> Não é possível definir o `Left` ou `Top` propriedade de um controle que esteja em linha com o texto.<br /><br /> Você não pode colocar controles em um cabeçalho ou rodapé, ou em um subdocumento.|  
|Eventos de controle|Quando o controle é selecionado, ela gera eventos na seguinte ordem:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Quando o controle estiver desmarcado, ela gera eventos na seguinte ordem:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Dimensionamento de controle|Quando você altera a configuração de zoom de um documento para algo diferente de 100%, os controles são desabilitados, embora eles aparecem para dimensionar com o documento. Por exemplo, se você clicar em um botão quando o documento está no zoom % 130, ele mostrará uma mensagem de que o controle foi desativado até que o zoom é definido como 100%. Os controles funcionará corretamente quando você alterar o zoom para 100%.|  
|Valores de propriedade de controle|Embora as propriedades de controles em um Windows Form são definidas como um valor inteiro, eles são definidos como um único para controles em um documento do Word. No Excel, os valores de propriedade dos controles são definidos para um duplo. Se o `Height` e `Width` propriedade de um controle em uma planilha excede o tamanho da planilha ou da tela, o valor é truncado.|  
|Redimensionamento de controle|Se você redimensiona um controle no documento usando um dos oito alças de dimensionamento, as novas dimensões do controle não são refletidas no **propriedades** janela até que o controle é remarcado.|  
|Comportamento de controle|Controles em uma planilha do Excel podem se comportar de forma imprevisível quando a janela de planilha é dividida. Por exemplo, acesso a um <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> na planilha pode estar disponível apenas em uma das janelas.|  
|Nomeação de controle|Você não pode usar palavras reservadas para controles de nome. Por exemplo, se você adicionar um <xref:Microsoft.Office.Tools.Excel.Controls.Button> em uma planilha e altere o nome para **sistema**, erros ocorrem quando você compilar o projeto.|  
|Programaticamente, adicionando controles|Não use o construtor do controle para adicionar um controle para o documento em tempo de execução. Em vez disso, use os métodos auxiliares fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por exemplo, usar o <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> para adicionar um botão em uma planilha. Se você quiser adicionar um controle que não há suporte para esses métodos auxiliares, você pode usar o método AddControl. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Controles de cópias|Se você copiar um controle de formulários do Windows e cole-o em um documento em tempo de execução, um contêiner vazio controle ActiveX será colado no documento. O controle de formulários do Windows não aparece no novo local e código atrás do controle original não é copiado para o contêiner de controle ActiveX.|  
  
## <a name="limitations-in-document-level-projects"></a>Limitações no nível de documento  
 Algumas limitações do uso de controles de Windows Forms em documentos são exclusivas a projetos no nível do documento.  
  
### <a name="control-support-at-design-time"></a>Suporte de controle em tempo de Design  
 Determinados controles de formulários do Windows são removidos do **caixa de ferramentas** quando uma planilha do Excel ou um documento do Word é aberto no designer do Visual Studio. Isso é devido a limitações técnicas ou porque a funcionalidade já está disponível no Word ou Excel. Suportam a todos os controles de formulários do Windows e outros componentes que aparecem em projetos do Excel e Word o **caixa de ferramentas** quando o documento tem o foco, e você também pode adicionar controles de terceiros para uma planilha ou documento.  
  
> [!NOTE]  
>  Todos os controles são removidos do **caixa de ferramentas** quando um documento está protegido. Para obter informações sobre proteção de documentos, consulte [proteção de documentos no nível do documento soluções](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  Controles de terceiros devem ter o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo definido como **true** para ser usada em uma solução do Office.  
  
 Os controles e componentes a seguir não estão disponíveis no **caixa de ferramentas**:  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### <a name="support-for-legacy-activex-controls"></a>Suporte para controles do ActiveX herdado  
 Se você criar um projeto do Office de nível de documento que usa um documento do Word existente ou a pasta de trabalho do Excel que contém os controles ActiveX, a funcionalidade dos controles ActiveX não é perdida; No entanto, não há nenhum suporte para a adição de novos controles ActiveX para seus documentos no Visual Studio. Por exemplo, se o seu documento do Word tem um botão do **controle** caixa de ferramentas que executa uma macro Visual Basic for Applications (VBA), ele continuará a executar a macro depois que o documento foi usado em um projeto do Office. No entanto, é recomendável que você remova os controles ActiveX e macros VBA e substituí-los com controles de formulários do Windows e código gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Controles em Visão geral de documentos do Office do Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Como adicionar controles do Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  