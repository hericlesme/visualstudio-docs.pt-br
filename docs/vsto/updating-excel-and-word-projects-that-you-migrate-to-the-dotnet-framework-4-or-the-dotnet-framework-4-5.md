---
title: "Atualizando projetos do Excel e Word que você migrar para o .NET Framework 4 ou o .NET Framework 4.5 | Microsoft Docs"
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
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 974071c68edd685bd23b29d6d37c520f50a78078
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="updating-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Atualizando projetos do Excel e do Word migrados para o .NET Framework 4 ou o .NET Framework 4.5
  Se você tiver um projeto do Excel ou Word que usa qualquer um dos seguintes recursos, você deve modificar seu código se a estrutura de destino for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior:  
  
-   [Métodos GetVstoObject e HasVstoObject](#GetVstoObject)  
  
-   [Classes geradas no nível de documento](#generatedclasses)  
  
-   [Controles de Windows Forms em documentos](#winforms)  
  
-   [Eventos de controle de conteúdo do Word](#ccevents)  
  
-   [Classes OLEObject e OLEControl](#ole)  
  
-   [Propriedade Controls.Item(Object)](#itemproperty)  
  
-   [Coleções que derivam de CollectionBase](#collections)  
  
 Você também deve remover o Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute e referências à classe Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy de projetos do Excel que são redirecionadas para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. O Visual Studio não remove esse atributo ou a referência de classe para você.  
  
## <a name="removing-the-excellocale1033-attribute-from-excel-projects"></a>Removendo o atributo ExcelLocale1033 de projetos do Excel  
 O Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute foi removido da parte do Visual Studio 2010 Tools para Office Runtime que é usado para soluções que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. O common language runtime (CLR) no [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e posteriormente sempre passa localidade 1033 ID para o modelo de objeto do Excel e você não pode usar esse atributo para desabilitar esse comportamento. Para obter mais informações, consulte [globalização e localização de soluções do Excel](../vsto/globalization-and-localization-of-excel-solutions.md).  
  
#### <a name="to-remove-the-excellocale1033attribute"></a>Para remover o ExcelLocale1033Attribute  
  
1.  Com o projeto aberto no Visual Studio, abra **Gerenciador de soluções**.  
  
2.  Sob o **propriedades** nó (c#) ou o **meu projeto** nó (para Visual Basic), clique duas vezes o arquivo de código AssemblyInfo para abri-lo no editor de códigos.  
  
    > [!NOTE]  
    >  Em projetos do Visual Basic, você deve clicar no **Mostrar todos os arquivos** no botão **Solution Explorer** para ver o arquivo de código AssemblyInfo.  
  
3.  Localize o Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute e remova-o arquivo ou comente-o.  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="removing-a-reference-to-the-excellocal1033proxy-class"></a>Removendo uma referência à classe ExcelLocal1033Proxy  
 Projetos que foram criados usando o Microsoft Visual Studio 2005 Tools para o Microsoft Office System instanciar o Excel <xref:Microsoft.Office.Interop.Excel.Application> objeto usando a classe Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy. Essa classe foi removida da parte do Visual Studio 2010 Tools para Office Runtime que usou para soluções que têm como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. Portanto, você deve remover ou comentar a linha de código que faz referência a essa classe.  
  
#### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Para remover a referência à classe ExcelLocal1033Proxy  
  
1.  Abra o projeto no Visual Studio e abra **Gerenciador de soluções**.  
  
2.  Em **Solution Explorer**, abra o menu de atalho para ThisAddin.cs (para c#) ou ThisAddIn (para Visual Basic) e, em seguida, escolha **Exibir código**.  
  
3.  No Editor de códigos, no `VSTO generated code` região, remover ou comentar a seguinte linha de código.  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a>Atualizando o código que usa os métodos HasVstoObject e GetVstoObject  
 Em projetos direcionados ao .NET Framework 3.5, os métodos GetVstoObject ou HasVstoObject estão disponíveis como métodos de extensão em um dos seguintes objetos nativo em seu projeto: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, ou <xref:Microsoft.Office.Interop.Excel.ListObject>. Quando você chamar esses métodos, você não precisa passar um parâmetro. O exemplo de código a seguir demonstra como usar o método GetVstoObject em um palavra VSTO suplemento que tem como alvo o .NET Framework 3.5.  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve modificar seu código para acessar esses métodos em uma das seguintes maneiras:  
  
-   Você ainda pode acessar esses métodos como métodos de extensão em <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, ou <xref:Microsoft.Office.Interop.Excel.ListObject> objetos. No entanto, agora você deve passar o objeto retornado pela propriedade Globals.Factory para esses métodos.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   Como alternativa, você pode acessar esses métodos no objeto que é retornado pela propriedade Globals.Factory. Quando você acessa esses métodos dessa forma, você deve passar o objeto nativo que você deseja estender para o método.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
##  <a name="generatedclasses"></a>Atualizando o código que usa instâncias das Classes geradas em projetos no nível de documento  
 Em projetos de nível de documento que o .NET Framework 3.5 de destino, as classes geradas nos projetos derivam as seguintes classes no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, os tipos no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] listadas acima são interfaces, em vez de classes. Classes gerado em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior derivam as seguintes classes de novo no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
 Se o código em seu projeto faz referência a uma instância de uma das classes geradas como a classe base que deriva de, você deve modificar o código.  
  
 Por exemplo, em um projeto de pasta de trabalho do Excel que tem como alvo o .NET Framework 3.5, você pode ter um método auxiliar que executa algum trabalho em instâncias do gerado `Sheet`  *n*  classes no seu projeto.  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)  
    ' Do something to the worksheet object.  
End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)  
{  
    // Do something to the worksheet object.  
}  
```  
  
 Se você redirecionar o projeto para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve fazer uma das seguintes alterações no seu código:  
  
-   Modificar qualquer código que chama o `DoSomethingToSheet` método para passar o <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> propriedade de um <xref:Microsoft.Office.Tools.Excel.WorksheetBase> objeto em seu projeto. Essa propriedade retorna um <xref:Microsoft.Office.Tools.Excel.Worksheet> objeto.  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   Modificar o `DoSomethingToSheet` parâmetro do método esperar um <xref:Microsoft.Office.Tools.Excel.WorksheetBase> do objeto em vez disso.  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)  
        ' Do something to the worksheet object.  
    End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)  
    {  
        // Do something to the worksheet object.  
    }  
    ```  
  
##  <a name="winforms"></a>Atualizar o código que usa o Windows Forms a controles em documentos  
 Você deve adicionar um **usando** (c#) ou **Imports** declaração (Visual Basic) para o <xref:Microsoft.Office.Tools.Excel> ou <xref:Microsoft.Office.Tools.Word> namespace para a parte superior de qualquer arquivo de código que usa a propriedade de controles para adicionar o Windows Forms controles para o documento ou a planilha programaticamente.  
  
 Em projetos direcionados ao .NET Framework 3.5, os métodos que adicionar controles de formulários do Windows (como o método AddButton) são definidos no <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> classes.  
  
 Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou versões posteriores, esses métodos são os métodos de extensão que estão disponíveis na propriedade de controles. Para usar esses métodos de extensão, o arquivo de código que você pode usar os métodos deve ter uma **usando** ou **Imports** instrução para o <xref:Microsoft.Office.Tools.Excel> ou <xref:Microsoft.Office.Tools.Word> namespace. Essa instrução é gerada automaticamente em novos projetos que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. No entanto, essa instrução não é adicionada automaticamente em projetos direcionados ao .NET Framework 3.5, você deve adicioná-lo ao redirecionar o projeto.  
  
 Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="ccevents"></a>Atualizando o código que manipula eventos de controle de conteúdo do Word  
 Em projetos direcionados ao .NET Framework 3.5, eventos de controles de conteúdo do Word são manipulados pelo genérica <xref:System.EventHandler%601> delegate. Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, esses eventos são tratados por outros delegados.  
  
 A tabela a seguir lista os eventos de controle de conteúdo do Word e delegados que estão associados com eles em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.  
  
|evento|Delegado a ser usado em [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e projetos posteriores|  
|-----------|---------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a>Atualizando o código que usa as Classes de OLEControl e OLEObject  
 Em projetos direcionados ao .NET Framework 3.5, você pode adicionar controles personalizados (por exemplo, controles de usuário do Windows Forms) para um documento ou a planilha usando as classes Microsoft.Office.Tools.Excel.OLEObject e Microsoft.Office.Tools.Word.OLEControl.  
  
 Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, essas classes foram substituídas pelo <xref:Microsoft.Office.Tools.Excel.ControlSite> e <xref:Microsoft.Office.Tools.Word.ControlSite> interfaces. Você deve modificar o código que se refere a Microsoft.Office.Tools.Excel.OLEObject e Microsoft.Office.Tools.Word.OLEControl em vez disso, consulte <xref:Microsoft.Office.Tools.Excel.ControlSite> e <xref:Microsoft.Office.Tools.Word.ControlSite>. Diferente de novos nomes, esses controles se comportam da mesma maneira que em projetos direcionados ao .NET Framework 3.5.  
  
 Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="itemproperty"></a>Atualizando o código que usa a propriedade Controls.Item(Object)  
 Em projetos direcionados ao .NET Framework 3.5, você pode usar a propriedade Item(Object) da coleção Microsoft.Office.Tools.Word.Document.Controls ou Microsoft.Office.Tools.Excel.Worksheet.Controls para determinar se um documento ou planilha tem um controle especificado.  
  
 Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, a propriedade Item(Object) foi removida dessas coleções. Para determinar se um documento ou a planilha contém um controle especificado, use o método Contains(System.Object) o <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> ou <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> coleção em vez disso.  
  
 Para obter mais informações sobre a coleção de controles de planilhas e documentos, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="collections"></a>Atualizando o código que usa coleções que derivam de CollectionBase  
 Em projetos direcionados ao .NET Framework 3.5, tipos de coleção várias no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derivam de <xref:System.Collections.CollectionBase> classe, como Microsoft.Office.Tools.SmartTagCollection, Microsoft.Office.Tools.Excel.ControlCollection, e Microsoft.Office.Tools.Word.ControlCollection.  
  
 Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, esses tipos de coleção agora são interfaces que não derivam <xref:System.Collections.CollectionBase>. Alguns membros não estão mais disponíveis nesses tipos de coleção, como <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>, e <xref:System.Collections.CollectionBase.InnerList%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Migrando soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Controles de conteúdo](../vsto/content-controls.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  