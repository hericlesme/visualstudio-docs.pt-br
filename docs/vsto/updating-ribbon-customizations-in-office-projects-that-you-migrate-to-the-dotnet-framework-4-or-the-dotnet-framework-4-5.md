---
title: "Atualizando personalizações da faixa de opções em projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5 | Microsoft Docs"
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
ms.openlocfilehash: 4d3c2e834b3a618bf033ef7f37ca8bbac7d0efcf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Atualizando personalizações da Faixa de Opções nos projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5
  Se o projeto contém uma personalização da faixa de opções que foi criada usando o **faixa de opções (Visual Designer)** item de projeto, você deve fazer as seguintes alterações para o código do projeto, se a estrutura de destino for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou mais tarde.  
  
-   Modificar o código gerado da faixa de opções.  
  
-   Modificar qualquer código que instancia os controles de faixa de opções em tempo de execução, que trata os eventos da faixa de opções ou define a posição de um componente de faixa de opções programaticamente.  
  
## <a name="updating-the-generated-ribbon-code"></a>Atualizando o código gerado da faixa de opções  
 Se a estrutura de destino do seu projeto será alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve alterar o código gerado para o item da faixa de opções, executando as etapas a seguir. Os arquivos de código que você precisa atualizar dependem da linguagem de programação e como você criou o projeto:  
  
-   Em projetos do Visual Basic, ou em projetos do Visual c# que você criou no [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] ou [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] executar todas as etapas no arquivo de code-behind a faixa de opções (*YourRibbonItem*. Designer.cs ou *YourRibbonItem*. VB). Para ver o arquivo code-behind em projetos do Visual Basic, clique o **Mostrar todos os arquivos** no botão **Gerenciador de soluções**.  
  
-   Em projetos Visual c# que você criou no Visual Studio 2008 e, em seguida, atualizado para [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], execute as duas primeiras etapas no arquivo de código da faixa de opções (*YourRibbonItem*. cs ou *YourRibbonItem*. vb), e Execute as etapas restantes no arquivo de code-behind a faixa de opções.  
  
#### <a name="to-change-the-generated-ribbon-code"></a>Para alterar o código gerado da faixa de opções  
  
1.  Modifique a declaração da classe da faixa de opções, de forma que deriva de <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> em vez de Microsoft.Office.Tools.Ribbon.OfficeRibbon.  
  
2.  Modificar o construtor da classe da faixa de opções, conforme mostrado abaixo. Se você adicionou seu próprio código para o construtor, não altere seu código. Em projetos do Visual Basic, modificar apenas o construtor sem parâmetros. Ignore o outro construtor.  
  
     O exemplo de código a seguir mostra o construtor padrão de uma classe de faixa de opções em um projeto que tem como destino o .NET Framework 3.5.  
  
    ```vb  
    Public Sub New()  
        MyBase.New()  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
    {  
        InitializeComponent();  
    }  
    ```  
  
     O exemplo de código a seguir mostra o construtor padrão de uma classe de faixa de opções em um projeto que tem como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.  
  
    ```vb  
    Public Sub New()  
        MyBase.New(Globals.Factory.GetRibbonFactory())  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
        : base(Globals.Factory.GetRibbonFactory())  
    {  
        InitializeComponent();  
    }  
    ```  
  
3.  No `InitializeComponent` método, modificar qualquer código que constrói um controle de faixa de opções para que o código em vez disso, use um dos métodos auxiliares do <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objeto.  
  
    > [!NOTE]  
    >  Em projetos do Visual c#, você deve expandir a região denominada `Component Designer generated code` para ver o `InitializeComponent` método.  
  
     Por exemplo, suponha que o arquivo contém a seguinte linha de código que instancia um <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> denominado `button1` em um projeto que tem como alvo o .NET Framework 3.5.  
  
    ```vb  
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();  
    ```  
  
     Em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve usar o código a seguir em vez disso.  
  
    ```vb  
    Me.button1 = Me.Factory.CreateRibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = this.Factory.CreateRibbonButton();  
    ```  
  
     Para obter uma lista completa dos métodos auxiliares para os controles de faixa de opções, consulte [Criando controles de faixa de opções](#ribboncontrols).  
  
4.  Em projetos do Visual c#, modifique qualquer linha de código no `InitializeComponent` método que usa um <xref:System.EventHandler%601> delegado para usar um delegado de faixa de opções específico em vez disso.  
  
     Por exemplo, suponha que o arquivo contém a seguinte linha de código que manipula o <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> evento em um projeto que tem como alvo o .NET Framework 3.5.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
     Em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve usar o código a seguir em vez disso.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
     Para obter uma lista completa de representantes de faixa de opções, consulte [manipulando eventos de faixa de opções](#ribbonevents).  
  
5.  Em projetos do Visual Basic, localize o `ThisRibbonCollection` classe no final do arquivo. Modifique a declaração da classe para que ele não herda de Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection.  
  
##  <a name="ribboncontrols"></a>Criando controles de faixa de opções  
 Você deve modificar qualquer código que instancia dinamicamente os controles de faixa de opções. Em projetos direcionados ao .NET Framework 3.5, controles de faixa de opções são classes que você pode instanciar diretamente em determinados cenários. Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou versões posteriores, esses controles são interfaces que você não pode instanciar diretamente. Você deve criar os controles usando métodos fornecidos pelo <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objeto.  
  
 Existem duas maneiras de acessar o objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   Usando a propriedade de fábrica de classe da faixa de opções. Use essa abordagem no código na classe Ribbon.  
  
-   Usando o método Globals.Factory.GetRibbonFactory. Use essa abordagem no código fora da classe Ribbon. Para obter mais informações sobre a classe globais, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 O exemplo de código a seguir demonstra como criar um <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> em uma classe de faixa de opções em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 A tabela a seguir lista os controles que você pode criar programaticamente e o método a ser usado para criar os controles nos projetos que visam o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.  
  
|Controle|Método RibbonFactory para usar na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e projetos posteriores|  
|-------------|---------------------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|  
  
##  <a name="ribbonevents"></a>Faixa de opções de manipulação de eventos  
 Você deve modificar qualquer código que trata os eventos de controles de faixa de opções. Em projetos direcionados ao .NET Framework 3.5, esses eventos são manipulados pelo genérica <xref:System.EventHandler%601> delegate. Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou versões posteriores, esses eventos estão agora controlados pelos outros delegados.  
  
 A tabela a seguir lista os eventos de faixa de opções e os delegados que estão associados com eles em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.  
  
|evento|Delegado a ser usado em [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e projetos posteriores|  
|-----------|---------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>evento em uma classe gerada da faixa de opções|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## <a name="setting-the-position-of-a-ribbon-component-programmatically"></a>Definir a posição de um componente de faixa de opções programaticamente  
 Você deve modificar qualquer código que define a posição de grupos, tabulações ou controles de faixa de opções. Em projetos direcionados ao .NET Framework 3.5, você pode usar os métodos AfterOfficeId e BeforeOfficeId da classe estática Microsoft.Office.Tools.Ribbon.RibbonPosition para atribuir a propriedade de posição de um grupo, uma guia ou um controle. Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve acessar esses métodos usando o <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> propriedade fornecida pelo <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objeto.  
  
 Existem duas maneiras de acessar o objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   Usando a propriedade de fábrica de classe da faixa de opções. Use essa abordagem no código na classe Ribbon.  
  
-   Usando o método Globals.Factory.GetRibbonFactory. Use essa abordagem no código fora da classe Ribbon. Para obter mais informações sobre a classe globais, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 O exemplo de código a seguir demonstra como definir a propriedade de posição de uma guia em uma classe de faixa de opções em um projeto que tem como destino o .NET Framework 3.5.  
  
```vb  
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");  
```  
  
 O exemplo de código a seguir demonstra a mesma tarefa em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
```vb  
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");  
```  
  
## <a name="see-also"></a>Consulte também  
 [Migrando soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Designer da faixa de opções](../vsto/ribbon-designer.md)  
  
  