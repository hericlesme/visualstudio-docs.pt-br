---
title: Controles de conteúdo
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0874ab1c883b7a56b7a031dc861949b05d9add56
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="content-controls"></a>Controles de conteúdo
  Controles de conteúdo fornecem uma maneira para você para documentos de design e os modelos que têm estes recursos:  
  
-   Uma interface de usuário (UI) que tem controlado a entrada como um formulário.  
  
-   Restrições que impedem que os usuários editem protegido seções do documento ou modelo. Para obter mais informações, consulte [proteger partes de documentos usando controles de conteúdo](#Protection).  
  
-   Associação de dados a uma fonte de dados. Para obter mais informações, consulte [ligar dados a controles de conteúdo](#DataBinding).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [usando o Visual Studio Tools para Office system (3.0) de controles de conteúdo de dados de ligação para Word 2007](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="overview-of-content-controls"></a>Visão geral dos controles de conteúdo  
 Controles de conteúdo fornecem uma interface do usuário que é otimizado para usuário entrada e impressão. Quando você adicionar um controle de conteúdo a um documento, o controle é identificado por uma borda, um título e texto temporário que pode fornecer instruções para o usuário. A borda e o título do controle não aparecem em versões impressas do documento.  
  
 Por exemplo, se desejar que o usuário insira uma data em uma seção do documento, você pode adicionar um controle de conteúdo de seletor de data para o documento. Quando os usuários clicam no controle, o seletor de data padrão da interface do usuário é exibida. Você também pode definir propriedades de controle para definir o calendário regional que é exibido e para especificar o formato de data. Depois que o usuário escolhe uma data, a interface do usuário do controle está oculto, e apenas a data será exibida se o usuário imprime o documento.  
  
 Controles de conteúdo também ajudam a fazer o seguinte:  
  
-   Impedir que usuários de edição ou exclusão de partes de um documento. Isso é útil se você tiver informações em um documento ou um modelo que os usuários devem ser capazes de ler, mas não editar, ou se você quiser que os usuários possam editar controles de conteúdo, mas não excluí-los.  
  
-   Associe partes de um documento ou um modelo de dados. Você pode associar controles de conteúdo para campos de banco de dados, objetos gerenciados no [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)], elementos XML que são armazenados no documento e outras fontes de dados.  
  
 Em projetos de nível de documento, você pode adicionar controles de conteúdo para o documento em tempo de design ou em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar controles de conteúdo para qualquer documento aberto em tempo de execução. Para obter mais informações, consulte [como: adicionar controles content a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Você pode usar controles de conteúdo apenas em documentos que são salvos no formato Open XML. Você não pode usar controles de conteúdo em documentos que são salvas no documento de Word 97-2003 (*. doc*) formato.  
  
## <a name="types-of-content-controls"></a>Tipos de controles de conteúdo  
 Há nove tipos diferentes de controles de conteúdo que você pode adicionar documentos. A maioria dos controles de conteúdo tem um tipo correspondente no <xref:Microsoft.Office.Tools.Word> namespace. Você também pode usar um genérico <xref:Microsoft.Office.Tools.Word.ContentControl>, que pode representar qualquer um dos controles de conteúdo disponíveis. Para uma explicação passo a passo que demonstra como usar cada um dos controles de conteúdo disponíveis, consulte [passo a passo: criar um modelo usando os controles de conteúdo](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
### <a name="build-block-gallery"></a>Criar galeria de blocos  
 Uma galeria de blocos de construção permite aos usuários selecionar em uma lista de *blocos de construção de documento* para inserir em um documento. Um bloco de construção de documento é uma parte do conteúdo que foi criado para ser usada várias vezes, como uma folha de rosto comum, uma tabela formatada ou um cabeçalho. Para obter mais informações, consulte o <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> tipo. Para obter mais informações sobre blocos de construção, consulte [o que há de novo para desenvolvedores no Word 2007](http://msdn.microsoft.com/en-us/74aa6688-65b3-4167-997d-131f26ad8f84).  
  
### <a name="check-box"></a>Caixa de seleção  
 Uma caixa de seleção fornece uma interface do usuário que representa um estado binário: marcada ou desmarcada.  
  
 Ao contrário de outros tipos de controles de conteúdo, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] não fornece um tipo específico que representa um controle de conteúdo da caixa de seleção. Em outras palavras, não há nenhum `CheckBoxContentControl` tipo. No entanto, você ainda pode criar um controle de conteúdo da caixa de seleção, adicionando um genérico <xref:Microsoft.Office.Tools.Word.ContentControl> para um documento programaticamente. Para obter mais informações, consulte [os controles de conteúdo da caixa de seleção em projetos do Word](#checkbox).  
  
### <a name="combo-box"></a>Caixa de combinação  
 Uma caixa de combinação exibe uma lista de itens que os usuários podem selecionar. Ao contrário de uma lista suspensa, a caixa de combinação permite que os usuários adicionem seus próprios itens. Para obter mais informações, consulte o <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> tipo.  
  
### <a name="date-picker"></a>seletor de data  
 Um seletor de data fornece um interface do usuário de calendário para selecionar uma data. O calendário será exibido quando o usuário final clicar na seta suspensa no controle. Você pode usar calendários regionais e formatos de data diferentes. Para obter mais informações, consulte o <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> tipo.  
  
### <a name="drop-down-list"></a>Lista suspensa  
 Uma lista suspensa exibe uma lista de itens que os usuários podem selecionar. Diferentemente de uma caixa de combinação, a lista suspensa não permite que os usuários adicionar ou editar itens. Para obter mais informações, consulte o <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> tipo.  
  
### <a name="group"></a>Grupo  
 Um controle de grupo define uma área protegida de um documento que os usuários não é possível editar ou excluir. Um controle de grupo pode conter qualquer item do documento, como texto, tabelas, gráficos e outros controles de conteúdo. Para obter mais informações, consulte o <xref:Microsoft.Office.Tools.Word.GroupContentControl> tipo.  
  
### <a name="picture"></a>Imagem  
 Um controle de imagem exibe uma imagem. Você pode especificar a imagem em tempo de design ou tempo de execução, ou os usuários podem clicar este controle para selecionar uma imagem a ser inserida no documento. Para obter mais informações, consulte o <xref:Microsoft.Office.Tools.Word.PictureContentControl> tipo.  
  
### <a name="rich-text"></a>RTF  
 Um controle rich text contém texto ou outros itens, como tabelas, imagens ou outros controles de conteúdo. Para obter mais informações, consulte o <xref:Microsoft.Office.Tools.Word.RichTextContentControl> tipo.  
  
### <a name="plain-text"></a>Texto sem formatação  
 Um controle de texto sem formatação contém texto. Um controle de texto sem formatação não pode conter outros itens, como tabelas, imagens ou outros controles de conteúdo. Além disso, todo o texto em um controle de texto sem formatação tem a mesma formatação. Por exemplo, se você colocar em itálico uma palavra de uma frase que está em um controle de texto sem formatação, todo o texto dentro do controle está em itálico. Para obter mais informações, consulte o <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> tipo.  
  
### <a name="generic-content-control"></a>Controle de conteúdo genérico  
 Um controle de conteúdo genérico é um <xref:Microsoft.Office.Tools.Word.ContentControl> objeto que pode representar qualquer um dos tipos disponíveis de controles de conteúdo. Você pode alterar um <xref:Microsoft.Office.Tools.Word.ContentControl> objeto para que atue como um tipo diferente de controle de conteúdo usando o <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> propriedade. Por exemplo, se você criar um <xref:Microsoft.Office.Tools.Word.ContentControl> do objeto que representa o controle de um texto sem formatação, você pode alterá-lo em tempo de execução para que ele se comporta como uma caixa de combinação.  
  
 Você pode criar <xref:Microsoft.Office.Tools.Word.ContentControl> objetos apenas em tempo de execução, não em tempo de design. Para obter mais informações, consulte [como: adicionar controles content a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
## <a name="common-features-of-content-controls"></a>Recursos comuns de controles de conteúdo  
 Controles de conteúdo mais compartilham um conjunto de membros que você pode usar para executar tarefas comuns. A tabela a seguir descreve algumas das tarefas que você pode executar usando esses membros.  
  
|Para esta tarefa:|Faça o seguinte:|  
|--------------------|--------------|  
|Obtém ou define o texto que é exibido no controle.|Use o **texto** propriedade. **Observação:** o <xref:Microsoft.Office.Tools.Word.PictureContentControl> e <xref:Microsoft.Office.Tools.Word.ContentControl> tipos não têm essa propriedade.|  
|Obtém ou define o texto temporário que é exibido no controle até que um usuário edita o controle, o controle é preenchido com dados de uma fonte de dados ou o conteúdo do controle é excluído.|Use o **PlaceholderText** propriedade. **Observação:** o <xref:Microsoft.Office.Tools.Word.PictureContentControl> tipo não tem essa propriedade.|  
|Obtém ou define o título exibido na borda do controle conteúdo quando o usuário clica neles.|Use o **título** propriedade.|  
|Remova o controle do documento automaticamente depois que o usuário edita o controle. (O texto no controle permanece no documento.)|Use o **temporário** propriedade.|  
|Execute código quando o usuário clica no controle de conteúdo, ou quando o cursor é movido para o controle de conteúdo por meio de programação.|Manipular o <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> eventos do controle.|  
|Execute código quando o usuário clica fora do controle de conteúdo, ou quando o cursor é movido para fora do controle de conteúdo por meio de programação.|Manipular o <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> eventos do controle.|  
|Executar código depois do controle de conteúdo é adicionado ao documento como resultado de uma operação de refazer ou desfazer a operação.|Manipular o <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> eventos do controle.|  
|Executar código antes do controle de conteúdo é excluído do documento.|Manipular o <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> eventos do controle.|  
  
##  <a name="Protection"></a> Proteger partes de documentos usando controles de conteúdo  
 Quando você protege uma parte de um documento, impedir que os usuários alterar ou excluir o conteúdo na parte do documento. Há várias maneiras que você pode proteger partes de um documento usando controles de conteúdo.  
  
 Se a área que você deseja proteger está dentro de um controle de conteúdo, você pode usar propriedades de controle de conteúdo para impedir que os usuários editar ou excluir o controle:  
  
-   O **LockContents** propriedade impede que os usuários editem o conteúdo.  
  
-   O **LockContentControl** propriedade impede que os usuários a exclusão do controle.  
  
 Se a área que você deseja proteger não está dentro de um controle de conteúdo, ou se você quiser proteger uma área que contém os controles de conteúdo e outros tipos de conteúdo, você pode colocar toda a área um <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Ao contrário de outros controles de conteúdo, um <xref:Microsoft.Office.Tools.Word.GroupContentControl> não fornece nenhuma interface do usuário que está visível para o usuário. Sua única finalidade é definir uma região em que os usuários não podem editar.  
  
> [!NOTE]  
>  Se você criar um <xref:Microsoft.Office.Tools.Word.GroupContentControl> que contém os controles de conteúdo incorporados, os controles de conteúdo inseridos não são protegidos automaticamente. Você deve usar o **LockContents** inseridos de propriedade de cada controle para impedir que os usuários editem o seu conteúdo.  
  
 Para obter mais informações sobre como usar os controles de conteúdo para proteger partes de documentos, consulte [como: proteger partes de documentos usando controles de conteúdo](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
##  <a name="DataBinding"></a> Associar dados a controles de conteúdo  
 Você pode exibir dados em documentos ao associar um controle de conteúdo para uma fonte de dados. Quando a fonte de dados é atualizada, o controle de conteúdo reflete as alterações. Você também pode salvar alterações de volta para a fonte de dados.  
  
 Controles de conteúdo fornecem as seguintes opções de associação de dados:  
  
-   Você pode vincular controles de conteúdo para os campos de banco de dados ou objetos gerenciados usando o mesmo modelo de associação de dados, como formulários do Windows.  
  
-   Você pode associar controles de conteúdo para os elementos em partes de XML (também chamado *partes XML personalizadas*) que são inseridos no documento.  
  
 Para obter uma visão geral de associação de controles de host em soluções do Office a dados, consulte [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### <a name="use-the-windows-forms-data-binding-model"></a>Use o modelo de associação de dados do Windows Forms  
 Suportam a controles de conteúdo mais o modelo de associação de dados simples que usa o Windows Forms. Associação de dados simples significa que um controle é vinculado a um elemento de dados simples, como um valor em uma coluna de uma tabela de dados. Para obter mais informações, consulte [associação de dados e o Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 Em projetos de nível de documento, você pode associar dados a controles de conteúdo usando o **fontes de dados** janela no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações sobre como adicionar controles de conteúdo de dados associados a documentos, consulte [como: preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md) e [como: preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
 A tabela a seguir lista os controles de conteúdo que você pode associar a cada tipo de dados de **fontes de dados** janela.  
  
|Tipo de dados|Controle de conteúdo padrão|Outros controles de conteúdo que pode ser associado a esse tipo de dados|  
|---------------|-----------------------------|----------------------------------------------------------------|  
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.Drawing.Image><br /><br /> Matriz <xref:System.Byte>|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Nenhum|  
  
 No nível de documento e projetos de suplemento do VSTO, você pode associar um controle de conteúdo para uma fonte de dados programaticamente, usando o <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> método o <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propriedade do controle. Se você fizer isso, passar a cadeia de caracteres **texto** para o *propertyName* parâmetro o <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> método. O **texto** propriedade é a propriedade de associação de dados padrão de controles de conteúdo.  
  
 Controles de conteúdo também oferecem suporte à associação de dados bidirecional, em que as alterações no controle são atualizadas para a fonte de dados. Para obter mais informações, consulte [como: atualizar uma fonte de dados com dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
> [!NOTE]  
>  Controles de conteúdo não dão suporte à associação de dados complexos. Se você vincular um <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ou <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> para uma fonte de dados usando o modelo de dados de formulários do Windows, os usuários verão apenas um único valor quando eles clicarem o controle. Se você quiser associar esses controles para um conjunto de valores de dados que os usuários podem escolher, você pode vincular esses controles a elementos em uma parte XML personalizada.  
  
### <a name="bind-content-controls-to-custom-xml-parts"></a>Vincular controles de conteúdo a partes XML personalizadas  
 Você pode vincular alguns controles de conteúdo para os elementos em partes XML personalizadas que são inseridos no documento. Para obter mais informações sobre partes XML personalizadas, consulte [visão geral de partes XML personalizadas](../vsto/custom-xml-parts-overview.md).  
  
 Para associar um controle de conteúdo a um elemento em uma parte XML personalizada, use o **XMLMapping** propriedade do controle. O exemplo de código a seguir demonstra como associar um <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> para o `Price` elemento sob o `Product` nó em uma parte XML personalizada que já foi adicionada ao documento.  
  
```vb  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")  
```  
  
```csharp  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);  
```  
  
 Para uma explicação passo a passo que demonstre como associar controles de conteúdo a partes XML personalizadas em mais detalhes, consulte [passo a passo: associar controles de conteúdo a partes XML personalizadas](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
 Quando você associa um controle de conteúdo a uma parte XML personalizada, associação de dados bidirecional é habilitada automaticamente. Se um usuário editar texto no controle, os elementos XML correspondentes são atualizados automaticamente. Da mesma forma, se os valores de elemento nas partes XML personalizadas são alterados, os controles de conteúdo que estão associados aos elementos XML exibirá os novos dados.  
  
 Você pode vincular os seguintes tipos de controles de conteúdo a partes XML personalizadas:  
  
-   <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PictureContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>  
  
### <a name="data-bind-events-for-content-controls"></a>Eventos para controles de conteúdo de associação de dados  
 Todos os controles de conteúdo fornecem um conjunto de eventos que você pode manipular para executar tarefas relacionadas a dados, como validar que o texto em um controle atenda a certos critérios antes de atualizar a fonte de dados. A tabela a seguir lista os eventos de controle de conteúdo relacionadas a associação de dados.  
  
|Tarefa|evento|  
|----------|-----------|  
|Execute código antes do Word atualiza automaticamente o texto em um controle de conteúdo que está associado a uma parte XML personalizada.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|  
|Executar código antes de palavra atualiza automaticamente os dados em uma parte XML personalizada que está associado a um conteúdo de controle (ou seja, depois que altera o texto no controle de conteúdo).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|  
|Execute seu próprio código para validar o conteúdo do controle de acordo com critérios personalizados.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|  
|Execute código depois do conteúdo do controle foi validado com êxito.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|  
  
## <a name="limitations-of-content-controls"></a>Limitações de controles de conteúdo  
 Quando você usa os controles de conteúdo em seus projetos do Office, lembre-se das limitações a seguir.  
  
### <a name="behavior-differences-between-design-time-and-runtime"></a>Diferenças de comportamento entre o tempo de execução e tempo de design  
 Muitas das limitações que o Microsoft Office Word impõe em controles de conteúdo em tempo de execução não são aplicadas em tempo de design. Quando você cria a interface do usuário de uma solução de nível de documento em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], modifique os controles de conteúdo somente de maneiras que têm suporte em tempo de execução.  
  
 Se você modificar um controle de conteúdo em tempo de design de forma que o controle não oferece suporte em tempo de execução, o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer não irá alertá-lo das alterações sem suporte. No entanto, quando você depura ou executa o projeto, ou se você salvar e, em seguida, reabra o projeto, o Word exibirá uma permissão de solicitação e a mensagem de erro para reparar o documento. Quando você repara o documento, Word remove todos os que não há suporte para conteúdo e a formatação do controle.  
  
 Por exemplo, o Word não impede que você adicione uma tabela para um <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> em tempo de design. No entanto, como <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> objetos não podem conter tabelas em tempo de execução, o Word exibirá uma mensagem de erro quando o documento for aberto.  
  
 Observe também que muitas propriedades que definem o comportamento de controles de conteúdo não têm efeito em tempo de design. Por exemplo, se você definir o **LockContents** propriedade de um controle de conteúdo para **True** em tempo de design, você ainda pode editar o texto do controle no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer. Essa propriedade só impede que os usuários editem o controle em tempo de execução.  
  
### <a name="event-limitations"></a>Limitações de evento  
 Controles de conteúdo não fornecem um evento que é gerado quando o usuário altera o texto ou outros itens no controle. Por exemplo, não há nenhum evento que é gerado quando um usuário seleciona um item diferente em uma <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ou <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
 Para determinar quando um usuário edita o conteúdo de um controle de conteúdo, você pode associar o controle a uma parte XML personalizada e, em seguida, tratar o <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> evento. Esse evento é gerado quando o usuário altera o conteúdo de um controle que está associado a uma parte XML personalizada. Para uma explicação passo a passo que demonstre como associar um controle de conteúdo a uma parte XML personalizada, consulte [passo a passo: associar controles de conteúdo a partes XML personalizadas](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
###  <a name="checkbox"></a> Controles de conteúdo de caixa de seleção em projetos do Word  
 Word 2010 introduziu um novo tipo de controle de conteúdo que representa uma caixa de seleção. No entanto, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] não fornece um tipo CheckBoxContentControl correspondente para uso em projetos do Office. Para criar um controle de conteúdo da caixa de seleção em uma [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou projeto do Word 2010, use o <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> método para criar um <xref:Microsoft.Office.Tools.Word.ContentControl> de objeto e passar o <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> valor para o método para especificar um controle de conteúdo da caixa de seleção. O exemplo de código a seguir demonstra como fazer isso.  
  
 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]  
  
## <a name="see-also"></a>Consulte também  
 [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Como: adicionar controles content a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Passo a passo: Criar um modelo usando os controles de conteúdo](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Dados em soluções do Office](../vsto/data-in-office-solutions.md)   
 [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
