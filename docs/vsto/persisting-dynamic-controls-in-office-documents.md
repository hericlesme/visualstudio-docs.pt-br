---
title: Persistindo dinâmico controles em documentos do Office | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 220a6e2c0b7e4633f91e7391448d27dddb5895c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="persisting-dynamic-controls-in-office-documents"></a>Mantendo controles dinâmicos em documentos do Office
  Controles que são adicionados em tempo de execução não são mantidos quando o documento ou a pasta de trabalho é salvo e fechada. O comportamento exato é diferente para controles de host e controles de formulários do Windows. Em ambos os casos, você pode adicionar código à sua solução para recriar os controles quando o usuário reabre o documento.  
  
 Controles que você adicionar a documentos em tempo de execução são chamados *controles dinâmicos*. Para obter mais informações sobre controles dinâmicos, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="persisting-host-controls-in-the-document"></a>Controles de Host persistindo no documento  
 Quando um documento é salvo e, em seguida, fechado, todos os controles de host dinâmico são removidos do documento. Somente nativo Office objetos subjacentes permanecem atrás. Por exemplo, um <xref:Microsoft.Office.Tools.Excel.ListObject> controle de host se torna um <xref:Microsoft.Office.Interop.Excel.ListObject>. Os objetos do Office nativo não estão conectados aos eventos de controle de host, e não têm a funcionalidade de associação de dados do controle de host.  
  
 A tabela a seguir lista o objeto nativo do Office que é deixado para trás em um documento para cada tipo de controle de host.  
  
|Tipo de controle de host|Tipo de objeto do Office nativo|  
|-----------------------|-------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### <a name="re-creating-dynamic-host-controls-when-documents-are-opened"></a>Criar controles de Host dinâmico novamente quando os documentos são abertos  
 Você pode recriar controles de host dinâmico no lugar de controles nativos existentes toda vez que um usuário abre o documento. Criar controles de host dessa maneira, quando um documento é aberto simula a experiência que os usuários podem esperar.  
  
 Para recriar um controle de host para o Word, ou um <xref:Microsoft.Office.Tools.Excel.NamedRange> ou <xref:Microsoft.Office.Tools.Excel.ListObject> controle de host para o Excel, use um `Add` \< *classe de controle*> método de um <xref:Microsoft.Office.Tools.Excel.ControlCollection> ou <xref:Microsoft.Office.Tools.Word.ControlCollection> objeto. Use um método que tem um parâmetro para o objeto nativo do Office.  
  
 Por exemplo, se você deseja criar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle de um nativo existente de host <xref:Microsoft.Office.Interop.Excel.ListObject> quando o documento for aberto, use o <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> método e passe existentes no <xref:Microsoft.Office.Interop.Excel.ListObject>. O exemplo de código a seguir demonstra isso em um projeto no nível de documento para Excel. O código cria um dinâmico novamente <xref:Microsoft.Office.Tools.Excel.ListObject> que se baseia em uma <xref:Microsoft.Office.Interop.Excel.ListObject> chamado `MyListObject` no `Sheet1` classe.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]  
  
### <a name="re-creating-charts"></a>Recriando gráficos  
 Para recriar um <xref:Microsoft.Office.Tools.Excel.Chart> hospedar um controle, você deve primeiro excluir nativo <xref:Microsoft.Office.Interop.Excel.Chart>e, em seguida, recrie o <xref:Microsoft.Office.Tools.Excel.Chart> usando o <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> ou <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> método. Não há nenhum `Add` \< *classe de controle*> método que permite que você crie um novo <xref:Microsoft.Office.Tools.Excel.Chart> com base em uma <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Se você não excluir primeiro nativo <xref:Microsoft.Office.Interop.Excel.Chart>, em seguida, você criará um gráfico de segundo, duplicado quando você recria o <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
## <a name="persisting-windows-forms-controls-in-documents"></a>Persistindo controles dos Windows Forms em documentos  
 Quando um documento é salvo e fechado, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] remove automaticamente todos os controles de formulários do Windows criados dinamicamente do documento. No entanto, o comportamento é diferente para o nível de documento e projetos de suplemento do VSTO.  
  
 Em personalizações no nível do documento, os controles e seus delimitadores ActiveX subjacentes (que são usadas para hospedar os controles no documento) são removidos na próxima vez em que o documento for aberto. Não há nenhuma indicação de que os controles foram já existe.  
  
 Em suplementos do VSTO, os controles são removidos, mas os wrappers de ActiveX permanecem no documento. Na próxima vez que o usuário abre o documento, os wrappers de ActiveX são visíveis. No Excel, os wrappers de ActiveX exibem imagens dos controles como apareceram a última vez em que o documento foi salvo. No Word, os wrappers de ActiveX são visíveis a menos que o usuário clica neles, caso em que eles exibem uma linha pontilhada que representa a borda dos controles. Há várias maneiras que você pode remover os wrappers de ActiveX. Para obter mais informações, consulte [removendo Wrappers de ActiveX em um suplemento](#removingActiveX).  
  
### <a name="re-creating-windows-forms-controls-when-documents-are-opened"></a>Recriando Windows controles de formulários quando os documentos são abertos  
 Você pode recriar excluídos controles de formulários do Windows quando o usuário reabre o documento. Para fazer isso, sua solução deve executar as seguintes tarefas:  
  
1.  Armazenar informações sobre o tamanho, o local e o estado dos controles quando o documento é salvo ou fechado. Uma personalização de nível de documento, você pode salvar esses dados para o cache de dados no documento. Um VSTO Add-in, você pode salvar esses dados a uma parte XML personalizada no documento.  
  
2.  Recrie os controles em um evento que é gerado quando o documento é aberto. Em projetos de nível de documento, você pode fazer isso no `Sheet` *n* `_Startup` ou `ThisDocument_Startup` manipuladores de eventos. Em projetos de suplemento do VSTO, você pode fazer nesse evento manipuladores para o <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> ou <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> eventos.  
  
###  <a name="removingActiveX"></a> Removendo Wrappers ActiveX em um suplemento  
 Quando você adicionar controles de formulários do Windows dinâmicos aos documentos usando um suplemento do VSTO, você pode impedir que os wrappers de ActiveX para os controles que aparecem no documento na próxima vez que ele está sendo usado das seguintes maneiras.  
  
#### <a name="removing-activex-wrappers-when-the-document-is-opened"></a>Removendo Wrappers ActiveX quando o documento é aberto.  
 Para remover todos os wrappers de ActiveX, chame o método GetVstoObject para gerar um item de host para o <xref:Microsoft.Office.Interop.Word.Document> ou <xref:Microsoft.Office.Interop.Excel.Workbook> que representa o documento aberto recentemente. Por exemplo, para remover todos os wrappers de ActiveX de um documento do Word, você pode chamar o método GetVstoObject para gerar um item de host para o <xref:Microsoft.Office.Interop.Word.Document> objeto que é passado para o manipulador de eventos para o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> evento.  
  
 Esse procedimento é útil quando você sabe que o documento será aberto apenas em computadores que têm o VSTO suplemento instalado. Se o documento pode ser passado para outros usuários que não têm o VSTO suplemento instalado, considere remover os controles antes de fechar o documento em vez disso.  
  
 O exemplo de código a seguir demonstra como chamar o método GetVstoObject quando o documento é aberto.  
  
 [!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
 [!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]  
  
 Embora o método GetVstoObject é usado principalmente para gerar um novo item de host em tempo de execução, esse método limpa também todos os wrappers de ActiveX do documento na primeira vez que ele é chamado de um documento específico. Para obter mais informações sobre como usar o método GetVstoObject, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Observe que se o suplemento do VSTO cria controles dinâmicos quando o documento for aberto, o suplemento do VSTO já chamará o método GetVstoObject como parte do processo para criar os controles. Você não precisa adicionar uma chamada separada para o método GetVstoObject para remover os wrappers de ActiveX nesse cenário.  
  
#### <a name="removing-the-dynamic-controls-before-the-document-is-closed"></a>Removendo os controles dinâmicos antes que o documento é fechado  
 O suplemento do VSTO pode remover explicitamente cada controle dinâmico do documento antes do documento é fechado. Esse procedimento é útil para documentos que podem ser passados para outros usuários que não têm o VSTO suplemento instalado.  
  
 O exemplo de código a seguir demonstra como remover todos os controles de formulários do Windows de um documento do Word, quando o documento é fechado.  
  
 [!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
 [!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]  
  
## <a name="see-also"></a>Consulte também  
 [Adicionando controles a documentos do Office no tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  