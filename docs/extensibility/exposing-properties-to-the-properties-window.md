---
title: Expondo propriedades na janela Propriedades | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 737ce6ae0368d7d1db9d72e6fb25355409663c09
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-properties-to-the-properties-window"></a>Expondo propriedades na janela Propriedades
Este passo a passo expõe as propriedades públicas de um objeto para o **propriedades** janela. As alterações feitas a essas propriedades são refletidas no **propriedades** janela.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Expondo propriedades na janela Propriedades  
 Nesta seção, você pode criar uma janela de ferramenta personalizada e exibir as propriedades públicas do objeto de painel de janela associada no **propriedades** janela.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Para expor as propriedades na janela Propriedades  
  
1.  Cada extensão do Visual Studio inicia com um projeto de implantação do VSIX que conterá os ativos de extensão. Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto VSIX chamado `MyObjectPropertiesExtension`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual C# / extensibilidade**.  
  
2.  Adicionar uma janela de ferramenta com a adição de um modelo de item da janela da ferramenta personalizada denominado `MyToolWindow`. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **caixa de diálogo Adicionar Novo Item**, vá para **itens do Visual C# / extensibilidade** e selecione **janela da ferramenta personalizada**. No **nome** campo na parte inferior da caixa de diálogo, altere o nome de arquivo para `MyToolWindow.cs`. Para obter mais informações sobre como criar uma janela de ferramenta personalizada, consulte [criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Abra MyToolWindow.cs e adicione a seguinte instrução using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Agora, adicione os campos a seguir para o `MyToolWindow` classe.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Adicione o seguinte código à classe MyToolWindow.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     O `TrackSelection` usos de propriedade `GetService` para obter um `STrackSelection` serviço, que fornece um <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface. O `OnToolWindowCreated` manipulador de eventos e `SelectList` método juntas criam uma lista de objetos selecionados que contém somente o ferramenta janela Painel próprio objeto. O `UpdateSelection` método informa o **propriedades** janela para exibir as propriedades públicas do painel de janela de ferramenta.  
  
6.  Compile o projeto e comece a depuração. A instância experimental do Visual Studio deve aparecer.  
  
7.  Se o **propriedades** janela não estiver visível, abri-la pressionando F4.  
  
8.  Abra o **MyToolWindow** janela. Você pode encontrar no **exibição / outras janelas**.  
  
     A janela é aberta e as propriedades públicas do painel da janela aparecem no **propriedades** janela.  
  
9. Alterar o **legenda** propriedade no **propriedades** janela para **propriedades do objeto meu**.  
  
     A legenda da janela MyToolWindow muda de acordo.  
  
## <a name="exposing-tool-window-properties"></a>Expondo propriedades da janela de ferramenta  
 Nesta seção, você adiciona uma janela de ferramenta e expor suas propriedades. As alterações feitas em propriedades serão refletidas no **propriedades** janela.  
  
#### <a name="to-expose-tool-window-properties"></a>Para expor as propriedades da janela de ferramenta  
  
1.  Abra MyToolWindow.cs e adicione a propriedade booliana pública IsChecked à classe MyToolWindow.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Essa propriedade obtém o estado da caixa de seleção do WPF criado posteriormente.  
  
2.  Abra MyToolWindowControl.xaml.cs e substitua o construtor MyToolWindowControl com o código a seguir.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Isso proporciona `MyToolWindowControl` acesse o `MyToolWindow` painel.  
  
3.  Em MyToolWindow.cs, altere o `MyToolWindow` construtor da seguinte maneira:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Altere para o modo de exibição de design de MyToolWindowControl.  
  
5.  O botão excluir e adicionar uma caixa de seleção de **caixa de ferramentas** para o canto superior esquerdo.  
  
6.  Adicione os eventos marcado e desmarcado. Selecione a caixa de seleção no modo de exibição de design. No **propriedades** janela, clique no botão de manipuladores de eventos (na parte superior direita do **propriedades** janela). Localizar **check** e tipo **checkbox_Checked** na caixa de texto, em seguida, localizar **desmarcado** e tipo **checkbox_Unchecked** na caixa de texto.  
  
7.  Adicione manipuladores de eventos de caixa de seleção:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Compile o projeto e comece a depuração.  
  
9. Na instância experimental, abra o **MyToolWindow** janela.  
  
     Pesquisar para propriedades da janela de **propriedades** janela. O **IsChecked** propriedade aparece na parte inferior da janela, sob o **propriedades do meu** categoria.  
  
10. Marque a caixa de seleção **MyToolWindow** janela. **IsChecked** no **propriedades** janela muda para **True**. Desmarque a caixa de seleção de **MyToolWindow** janela. **IsChecked** no **propriedades** janela muda para **False**. Alterar o valor de **IsChecked** no **propriedades** janela. Caixa de seleção de **MyToolWindow** alterações de janela para coincidir com o novo valor.  
  
    > [!NOTE]
    >  Se você deve descartar um objeto que é exibido no **propriedades** janela, chamada `OnSelectChange` com um `null` contêiner de seleção primeiro. Depois de descartar a propriedade ou o objeto, você pode alterar para um contêiner de seleção que foi atualizado <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> e <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> lista.  
  
## <a name="changing-selection-lists"></a>Alterando a lista de seleção  
 Nesta seção, você adiciona uma lista de seleção para uma classe de propriedade básico e usa a interface de janela de ferramenta para escolher qual lista de seleção para exibir.  
  
#### <a name="to-change-selection-lists"></a>Para alterar a seleção de lista  
  
1.  Abra MyToolWindow.cs e adicione uma classe pública chamada `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Adicionar uma propriedade SimpleObject para a classe MyToolWindow, além de dois métodos para alternar o **propriedades** seleção janela entre o painel de janela e `Simple` objeto.  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  No MyToolWindowControl.cs, substitua os manipuladores de caixa de seleção com estas linhas de código:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Compile o projeto e comece a depuração.  
  
5.  Na instância experimental, abra o **MyToolWindow** janela.  
  
6.  Marque a caixa de seleção no **MyToolWindow** janela. O **propriedades** janela exibe o `Simple` propriedades do objeto **SomeText** e **ReadOnly**. Desmarque a caixa de seleção. As propriedades públicas da janela aparecem no **propriedades** janela.  
  
    > [!NOTE]
    >  O nome de exibição **SomeText** é **meu texto**.  
  
## <a name="best-practice"></a>Prática recomendada  
 Neste passo a passo, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> é implementado para que a coleção do objeto selecionável e a coleção do objeto selecionado são a mesma coleção. Apenas o objeto selecionado aparece na lista de navegador de propriedade. Para uma implementação de ISelectionContainer mais completa, consulte os exemplos de Reference.ToolWindow.  
  
 Janelas de ferramentas do Visual Studio persistem entre sessões do Visual Studio. Para obter mais informações sobre como manter o estado da janela de ferramenta, consulte <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Consulte também  
 [Estender propriedades e a janela de propriedades](../extensibility/extending-properties-and-the-property-window.md)