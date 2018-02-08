---
title: "Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: 71f0837bbc488518204e8b9336339c2d01c21600
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF

Este passo a passo fornece uma introdução ao desenvolvimento no WPF (Windows Presentation Foundation). Você vai criar um aplicativo básico que inclui elementos comuns à maioria dos aplicativos de área de trabalho do WPF: marcação de XAML, code-behind, definições de aplicativo, controles, layout, vinculação de dados e estilos.

## <a name="creating-the-application-project"></a>Criar o projeto de aplicativo

Nesta seção, você criará a infraestrutura do aplicativo, que inclui o projeto e uma janela ou um formulário principal.

### <a name="to-create-the-project"></a>Para criar o projeto

1. Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto**.

1. Na caixa de diálogo **Novo Projeto**, expanda o nó **Visual C#** ou **Visual Basic** e escolha o nó **Windows**, depois expanda o nó **Windows** e escolha o nó **Área de trabalho clássica**.

1. Na lista de modelos, escolha o modelo **Aplicativo WPF**.

1. Na caixa de texto **Nome** insira `ExpenseIt` e, em seguida, escolha o botão **OK**.

    O projeto é criado e os arquivos do projeto são adicionados ao **Gerenciador de Soluções** e o designer da janela do aplicativo padrão **MainWindow.xaml** é exibido.

### <a name="to-modify-the-main-window"></a>Para modificar a janela principal

1. No designer, escolha a guia **MainWindow.xaml** se ela ainda não for a guia ativa do designer.

1. Se estiver usando C#, localize a linha `<Window x:Class="ExpenseIt.MainWindow"` e substitua-a por `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.
  
     Se estiver usando o Visual Basic, localize a linha `<Window x:Class=" MainWindow"` e substitua-a por `<NavigationWindow x:Class="MainWindow"`.
  
     Observe que quando você altera a marca `<Window` para `<NavigationWindow`, o IntelliSense altera automaticamente a marca de fechamento para `</NavigationWindow>` também.
  
    > [!NOTE]
    >  Depois de alterar a marca, se a janela **Lista de Erros** estiver aberta, você poderá notar vários erros. Não se preocupe, as alterações feitas nas próximas etapas farão com que eles desapareçam.

1. Escolha as marcas `<Grid>` e `</Grid>`, e exclua-as.
  
     Uma **NavigationWindow** não pode conter outros elementos de interface do usuário, como uma **Grade**.

1. Na janela **Propriedades**, expanda o nó de categoria **Comum**, escolha a propriedade **Título** e, em seguida, insira `ExpenseIt` e pressione a tecla **Enter**.
  
     Observe que o elemento **Título** na janela do XAML é alterado para corresponder ao novo valor. Você pode modificar as propriedades de XAML na janela XAML ou na janela **Propriedades** e as alterações são sincronizadas.

1. Na janela XAML, defina o valor do elemento **Altura** como `375` e defina o valor da propriedade **Largura** como `500`.
  
     Esses elementos correspondem às propriedades **Altura** e **Largura**, encontradas na categoria **Layout** na janela **Propriedades**.
  
     O arquivo **MainWindow.xaml** agora deve ter essa aparência em C#:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">
    </NavigationWindow>  
    ```

    Ou essa, no Visual Basic:

    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">    
    </NavigationWindow>  
    ```  

### <a name="to-modify-the-code-behind-file-c"></a>Para modificar o arquivo code- (C#)

1. No **Gerenciador de Soluções**, expanda o nó **MainWindow.xaml** e abra o arquivo **MainWindow.xaml.cs**.

1. Localize a linha `public partial class MainWindow : Window` e substitua-a por `public partial class MainWindow : NavigationWindow`.

    Isso altera a classe `MainWindow` para derivar de `NavigationWindow`. No Visual Basic, isso ocorre automaticamente quando você altera a janela no XAML, portanto, nenhuma alteração de código é necessária.

## <a name="adding-files-to-the-application"></a>Adicionar arquivos ao aplicativo

Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.

### <a name="to-add-a-home-screen"></a>Para adicionar uma tela inicial

1. No **Gerenciador de Soluções**, abra o menu de atalho para o nó **ExpenseIt** e escolha **Adicionar** > **Página**.

1. Na caixa de diálogo **Adicionar Novo Item**, escolha a caixa de texto **Nome**, insira `ExpenseItHome` e escolha o botão **Adicionar**.
  
     Esta página é a primeira janela que é exibida quando o aplicativo é iniciado.

1. No designer, escolha a guia **ExpenseItHome.xaml** se ela ainda não for a guia ativa do designer.

1. Escolha o elemento `<Title>` e altere o título para **ExpenseIt – Início**.
  
     O arquivo **ExpenseItHome.xaml** agora deve ter essa aparência em C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">    
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
    No Visual Basic, a primeira linha será um pouco diferente:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
    ```  

1. No designer, escolha a guia **MainWindow.xaml**.

1. Localize o elemento de linha `Title="ExpenseIt" Height="375" Width="500">` e adicione uma propriedade `Source="ExpenseItHome.xaml"`.
  
     Isso define **ExpenseItHome.xaml** como a primeira página aberta quando o aplicativo é iniciado. O arquivo **MainWindow.xaml** agora deve ter essa aparência em C#:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">    
    </NavigationWindow>  
    ```  
  
    No Visual Basic, a primeira linha será um pouco diferente:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"
    ```  
  
     Como as propriedades definidas anteriormente, você pode definir a propriedade `Source` na categoria **Diversos** da janela **Propriedades**.
  
### <a name="to-add-a-details-window"></a>Para adicionar uma janela de detalhes

1. No **Gerenciador de Soluções**, abra o menu de atalho para o nó **ExpenseIt** e escolha **Adicionar** > **Página**.

1. Na caixa de diálogo **Adicionar Novo Item**, escolha a caixa de texto **Nome**, insira `ExpenseReportPage` e escolha o botão **Adicionar**.
  
     Essa janela exibirá um relatório de despesas individuais.

1. No designer, escolha a guia **ExpenseReportPage.xaml** se ela ainda não for a guia ativa do designer.

1. Escolha o elemento `<Title>` e altere o título para **ExpenseIt – Exibir despesa**.
  
     O arquivo ExpenseReportPage.xaml agora deve ter essa aparência em C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">    
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
    No Visual Basic, a primeira linha será um pouco diferente:  
  
    ```xaml  
    <Page x:Class="ExpenseReportPage"  
    ```  

1. Na barra de menus, escolha **Depurar** > **Iniciar Depuração** (ou pressione **F5**) para executar o aplicativo.
  
     A ilustração a seguir mostra o aplicativo com os botões da janela de navegação.
  
     ![Captura de tela de exemplo de ExpenseIt](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")

1. Feche o aplicativo para retornar ao modo de design.

## <a name="creating-the-user-interface"></a>Criar a interface do usuário

O layout oferece uma maneira ordenada de posicionar elementos e também gerencia o tamanho e a posição desses elementos quando um formulário é redimensionado. Nesta seção, você criará uma grade com uma única coluna e três linhas. Você adicionará controles às duas páginas, adicionará um pouco de código e finalmente definirá estilos reutilizáveis para os controles.

### <a name="to-create-the-layout"></a>Para criar o layout

1. Abra **ExpenseItHome.xaml** e escolha o elemento `<Grid>`.

1. Na janela **Propriedades**, expanda o nó da categoria **Layout** e defina os valores de **Margem** como `10`, `10`, `0` e `10`, que correspondem às margens esquerda, direita, superior e inferior.

     O elemento `Margin="10,0,10,10"` é adicionado ao `<Grid>` elemento no XAML. Mais uma vez, você poderia inserir esses valores diretamente no código XAML em vez de usar a janela **Propriedades**, com o mesmo resultado.

1. Adicione o seguinte código XAML ao elemento `Grid` para criar as definições de linha e coluna:

    ```xaml  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition />  
        <RowDefinition Height="Auto"/>  
    </Grid.RowDefinitions>  
    ```

### <a name="to-add-controls"></a>Para adicionar controles

1. Abra **ExpenseItHome.xaml**.

1. Adicione o seguinte código XAML logo acima da marca `</Grid>` para criar os controles `Border`, `ListBox` e `Button`:  

    ```xaml  
    <!-- People list -->  
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">  
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
      </Border>  
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">  
          <ListBoxItem>Mike</ListBoxItem>  
          <ListBoxItem>Lisa</ListBoxItem>  
          <ListBoxItem>John</ListBoxItem>  
          <ListBoxItem>Mary</ListBoxItem>  
      </ListBox>

      <!-- View report button -->
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
    ```

     Observe que os controles aparecem na janela de design. Você pode também criar os controles arrastando-as da janela **Caixa de ferramentas** para a janela de design e definir suas propriedades na janela **Propriedades**.

1. Crie e execute o aplicativo. A ilustração a seguir mostra a aparência do tempo de execução dos controles criados pelo XAML nesse procedimento.

     ![Captura de tela de exemplo de ExpenseIt](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")  

1. Feche o aplicativo para retornar ao modo de design.

### <a name="to-add-a-background-image"></a>Para adicionar uma imagem como tela de fundo

1. Escolha a imagem a seguir e salve-a como `watermark.png`.

     ![Imagem de marca-d'água para instruções passo a passo](../designers/media/wpf_watermark.png "watermark")  

    > [!NOTE]
    >  Como alternativa, você pode criar sua própria imagem e salvá-la como `watermark.png`.

1. No **Gerenciador de Soluções**, abra o menu de atalho para o nó **ExpenseIt** e escolha **Adicionar** > **Item Existente**.

1. Na caixa de diálogo **Adicionar Item Existente** encontre a imagem **watermark.png** que você acabou de adicionar, selecione-a e, em seguida, escolha o botão **Adicionar**.

    > [!NOTE]
    >  Você pode precisar expandir a lista **Tipos de Arquivo** e escolher **Arquivos de Imagem**.

1. Abra o arquivo **ExpenseItHome.xaml** e adicione o seguinte código XAML logo acima da marca `</Grid>` para criar uma imagem de tela de fundo:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png"/>
    </Grid.Background>
    ```

### <a name="to-add-a-title"></a>Para adicionar um título

1. Abra **ExpenseItHome.xaml**.

1. Localize a linha `<Grid.ColumnDefinitions>` e adicione o seguinte abaixo dela:

    ```xaml
    <ColumnDefinition Width="230" />
    ```

    Isso cria uma coluna adicional à esquerda das outras colunas com uma largura fixa de 230 pixels.

1. Localize a linha `<Grid.RowDefinitions>` e adicione o seguinte abaixo dela:  

    ```xaml
    <RowDefinition />
    ```

    Isso adiciona uma linha à parte superior da grade.

1. Mova os controles para a segunda coluna, definindo o valor `Grid.Column` como 1. Mova cada controle para baixo uma linha, aumentando cada valor `Grid.Row` em 1.

    1. Localize a linha `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Altere `Grid.Column="0"` para `Grid.Column="1"` e `Grid.Row="0"` para `Grid.Row="1"`.

    1. Localize a linha `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Altere `Grid.Column="0"` para `Grid.Column="1"` e `Grid.Row="1"` para `Grid.Row="2"`.

    1. Localize a linha `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Altere `Grid.Column="0"` para `Grid.Column="1"` e `Grid.Row="2"` para `Grid.Row="3"`.

1. Antes do elemento `<Border`, adicione o seguinte código XAML para exibir o título:

    ```xaml
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        View Expense Report
    </Label>
    ```

     O conteúdo de **ExpenseItHome.xaml** agora deve ter essa aparência em C#:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
    No Visual Basic, a primeira linha será um pouco diferente:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
    ```  

1. Se você compilar e executar o aplicativo neste ponto, ele deverá se parecer com a seguinte ilustração:  
  
     ![Captura de tela de exemplo de ExpenseIt](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")  

### <a name="to-add-code-to-the-button"></a>Para adicionar código ao botão

1. Abra **ExpenseItHome.xaml**.

1. Escolha o elemento `Button` e adicione o seguinte código XAML logo após o elemento `HorizontalAlignment="Right"`: `Click="Button_Click"`.
  
     Isso adiciona um manipulador de eventos ao evento `Click` do botão. Agora, código do elemento **Botão** deve estar assim:  
  
    ```xaml  
    <!-- View report button -->  
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>  
    ```  

1. Abra o arquivo **ExpenseItHome.xaml.cs** ou **ExpenseItHome.xaml.vb**.

1. Adicione o seguinte código à classe `ExpenseItHome`:  
  
   ```csharp  
   private void Button_Click(object sender, RoutedEventArgs e)  
   {  
       // View Expense Report  
       ExpenseReportPage expenseReportPage = new ExpenseReportPage();  
       this.NavigationService.Navigate(expenseReportPage);    
   }  
   ```  
  
   ```vb  
   Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
       ' View Expense Report  
       Dim expenseReportPage As New ExpenseReportPage()  
   Me.NavigationService.Navigate(expenseReportPage)  
   End Sub  
   ```

    Esse manipulador de eventos abre a página Relatório de Despesas quando o botão é clicado.

### <a name="to-create-the-ui-for-the-report-page"></a>Para criar a interface do usuário para a página de relatório

1. Abra **ExpenseReportPage.xaml**.

    Esta página exibe o relatório de despesas da pessoa selecionada na home page.

1. Adicione o seguinte código XAML entre as marcas `<Grid>` e `</Grid>`:

    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.ColumnHeaderStyle>  
                    <Style TargetType="{x:Type DataGridColumnHeader}">  
                        <Setter Property="Height" Value="35" />  
                        <Setter Property="Padding" Value="5" />  
                        <Setter Property="Background" Value="#4E87D4" />  
                        <Setter Property="Foreground" Value="White" />  
                    </Style>  
                </DataGrid.ColumnHeaderStyle>  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
    ```  
  
     Essa interface do usuário é semelhante à criada para a home page, mas os dados do relatório são exibidos em um controle de **DataGrid**.

1. Crie e execute o aplicativo.

1. Escolha o botão **Exibir**.
  
     A página de relatório de despesas é exibida.
  
     A ilustração a seguir mostra a página Relatório de Despesas. Observe que o botão de navegação regressiva está habilitado.
  
     ![Captura de tela de exemplo de ExpenseIt](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
### <a name="to-style-controls"></a>Para controles de estilo  

1. Abra o arquivo **App.xaml** (C#) ou **Application.xaml** (Visual Basic).

1. Adicione o seguinte XAML entre as marcas `<Application.Resources>` e `</Application.Resources>`:  
  
    ```xaml  
    <!-- Header text style -->  
    <Style x:Key="headerTextStyle">  
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>  
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>  
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>  
        <Setter Property="Label.FontSize" Value="18"></Setter>  
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>  
    </Style>  
  
    <!-- Label style -->  
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">  
        <Setter Property="VerticalAlignment" Value="Top" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
        <Setter Property="FontWeight" Value="Bold" />  
        <Setter Property="Margin" Value="0,0,0,5" />  
    </Style>  
  
    <!-- DataGrid header style -->  
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
        <Setter Property="Foreground" Value="White" />  
    </Style>  
  
    <!-- List header style -->  
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
    </Style>  
  
    <!-- List header text style -->  
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">  
        <Setter Property="Foreground" Value="White" />  
        <Setter Property="VerticalAlignment" Value="Center" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
    </Style>  
  
    <!-- Button style -->  
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">  
        <Setter Property="Width" Value="125" />  
        <Setter Property="Height" Value="25" />  
        <Setter Property="Margin" Value="0,10,0,0" />  
        <Setter Property="HorizontalAlignment" Value="Right" />  
    </Style>  
    ```  
  
     Esse XAML adiciona os seguintes estilos:  
  
    -   `headerTextStyle`: para formatar o título da página `Label`.
  
    -   `labelStyle`: para formatar os controles `Label`.
  
    -   `columnHeaderStyle`: para formatar o `DataGridColumnHeader`.
  
    -   `listHeaderStyle`: para formatar os controles `Border` do cabeçalho da lista.
  
    -   `listHeaderTextStyle`: para formatar o **Rótulo** do cabeçalho.
  
    -   `buttonStyle`: para formatar o `Button` na página **ExpenseItHome.xaml**.

1. Abra **ExpenseItHome.xaml** e substitua tudo entre os elementos `<Grid>` e `</Grid>` pelo seguinte XAML:  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
  
            <Grid.RowDefinitions>  
                <RowDefinition/>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >  
                View Expense Report  
            </Label>  
            <!-- People list -->  
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">  
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>  
            </Border>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"  />  
            </Grid.Background>  
    ```  
  
     As propriedades como `VerticalAlignment` e `FontFamily` que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos.

1. Abra **ExpenseReportPage.xaml** e substitua tudo entre os elementos `<Grid>` e `</Grid>` final pelo seguinte XAML:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Name:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"   
    Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Department:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"   
                      AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>    
    ```  
  
     Isso adiciona estilos aos elementos `<Label>` e `<Border>`.
  
## <a name="connecting-to-data"></a>Conectando-se a Dados  
 Nesta seção, você criará um provedor de dados e um modelo de dados e conectará os controles para exibir os dados.
  
### <a name="to-bind-data-to-a-control"></a>Para associar dados a um controle

1. Abra **ExpenseItHome.xaml** e escolha o elemento `<Grid>`.

1. Adicione o seguinte código XAML:  
  
    ```xaml    
    <Grid.Resources>  
    <!-- Expense Report Data -->  
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">  
        <x:XData>  
            <Expenses xmlns="">  
                <Person Name="Mike" Department="Legal">  
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />  
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />  
                </Person>  
                <Person Name="Lisa" Department="Marketing">  
                    <Expense ExpenseType="Document printing"  
          ExpenseAmount="50"/>  
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />  
                </Person>  
                <Person Name="John" Department="Engineering">  
                    <Expense ExpenseType="Magazine subscription"   
         ExpenseAmount="50"/>  
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />  
                    <Expense ExpenseType="Software" ExpenseAmount="500" />  
                </Person>  
                <Person Name="Mary" Department="Finance">  
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />  
                </Person>  
            </Expenses>  
        </x:XData>  
    </XmlDataProvider>  
    </Grid.Resources>  
    ```  
  
     Esse código cria uma classe `XmlDataProvider` que contém os dados de cada pessoa. Normalmente, isso seria carregado como um arquivo, mas para simplificar, os dados são adicionados embutidos.

1. Dentro do elemento `<Grid.Resources>`, adicione o seguinte código XAML:  
  
    ```xaml  
    <!-- Name item template -->  
    <DataTemplate x:Key="nameItemTemplate">  
        <Label Content="{Binding XPath=@Name}"/>  
    </DataTemplate>  
    ```  
  
     Isso adiciona um `Data Template` que define como exibir os dados na **Caixa de Listagem**.

1. Substitua o elemento existente `<ListBox>` pelo seguinte XAML:  
  
    ```xaml  
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"   
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"  
             ItemTemplate="{StaticResource nameItemTemplate}">  
    </ListBox>  
    ```  
  
     Esse código associa a propriedade `ItemsSource` de `ListBox` à fonte de dados e aplica o modelo de dados como o `ItemTemplate`.
  
### <a name="to-connect-data-to-controls"></a>Para conectar dados aos controles  

1. Abra **ExpenseReportPage.xaml.vb** ou **ExpenseReportPage.xaml.cs**.

1. No C#, adicione o seguinte construtor à classe **ExpenseReportPage** ou, no Visual Basic, substitua a classe existente pelo seguinte:  
  
   ```csharp  
   // Custom constructor to pass expense report data  
   public ExpenseReportPage(object data):this()  
   {  
       // Bind to expense report data.
       this.DataContext = data;  
   }  
   ```  
  
   ```vb  
   Partial Public Class ExpenseReportPage  
   Inherits Page  
       Public Sub New()  
       InitializeComponent()  
       End Sub  
  
       ' Custom constructor to pass expense report data  
       Public Sub New(ByVal data As Object)  
           Me.New()  
           ' Bind to expense report data.
           Me.DataContext = data  
       End Sub    
   End Class  
   ```  
  
   Este construtor aceita um objeto de dados como um parâmetro. Nesse caso, o objeto de dados conterá o nome da pessoa selecionada.

1. Abra **ExpenseItHome.xaml.vb** ou **ExpenseItHome.xaml.cs**.

1. Substitua o código do manipulador de eventos `Click` pelo seguinte:  
  
   ```csharp  
   private void Button_Click(object sender, RoutedEventArgs e)  
   {  
       // View Expense Report  
       ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);  
       this.NavigationService.Navigate(expenseReportPage);    
   }  
   ```  
  
   ```vb  
   Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
       ' View Expense Report  
       Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)  
       Me.NavigationService.Navigate(expenseReportPage)  
   End Sub  
   ```  
  
   Esse código chama o novo construtor.
  
### <a name="to-update-the-ui-with-data-templates"></a>Para atualizar a interface do usuário com modelos de dados  

1. Abra **ExpenseReportPage.xaml**.

1. Substitua o código XAML dos elementos **Nome** e **Departamento**`<StackPanel` pelo seguinte:  
  
    ```xaml  
    <!-- Name -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Name:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>  
    </StackPanel>  
  
    <!-- Department -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Department:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>  
    </StackPanel>    
    ```  
  
     Isso associa os controles do **Rótulo** às propriedades da fonte de dados apropriada.

1. Adicione o seguinte código XAML dentro do elemento `<Grid>`:  
  
    ```xaml  
    <!--Templates to display expense report data-->  
    <Grid.Resources>  
        <!-- Reason item template -->  
        <DataTemplate x:Key="typeItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseType}"/>  
        </DataTemplate>  
        <!-- Amount item template -->  
        <DataTemplate x:Key="amountItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseAmount}"/>  
        </DataTemplate>  
    </Grid.Resources>    
    ```  
  
     Isso define como exibir os dados do relatório de despesas.

1. Substitua o elemento `<DataGrid>` pelo seguinte:  
  
    ```xaml  
    <!-- Expense type and Amount table -->  
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >  
  
        <DataGrid.Columns>  
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />  
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />  
        </DataGrid.Columns>  
  
    </DataGrid>  
    ```  
  
     Isso adiciona uma **ItemSource** e define as associações para os itens de despesa.

1. Crie e execute o aplicativo.

1. Escolha uma pessoa e, em seguida, escolha o botão **Exibir**.
  
     A ilustração a seguir mostra as duas páginas do aplicativo ExpenseIt com controles, layout, estilos, vinculação de dados e modelos de dados aplicados.
  
     ![Capturas de tela de exemplo de ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="best-practices"></a>Práticas recomendadas  

Este exemplo demonstra os fundamentos do WPF e, consequentemente, não segue as práticas recomendadas de desenvolvimento de aplicativos. Para obter uma cobertura abrangente das práticas recomendadas de desenvolvimento dos aplicativos WPF e .NET Framework, consulte os tópicos a seguir, conforme apropriado:  
  
-   Acessibilidade – [Práticas recomendadas de acessibilidade](/dotnet/framework/ui-automation/accessibility-best-practices)  
  
-   Segurança – [Segurança do Windows Presentation Foundation](/dotnet/framework/wpf/security-wpf)  
  
-   Localização – [Visão geral de globalização e localização do WPF](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)  
  
-   Desempenho – [Otimizando o desempenho do aplicativo WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)  
  
## <a name="whats-next"></a>O que vem a seguir  

Agora você tem uma série de técnicas à sua disposição para criar um aplicativo da área de trabalho usando o WPF. Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo do WPF limitado por dados. Este tópico não é exaustivo, mas dará a você uma noção de algumas das possibilidades que você pode descobrir por conta própria, além das técnicas do tópico.
  
Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:  
  
-   [Arquitetura do WPF](/dotnet/framework/wpf/advanced/wpf-architecture)  
  
-   [Visão geral do XAML](/dotnet/framework/wpf/advanced/xaml-overview-wpf)  
  
-   [Visão geral das propriedades da dependência](/dotnet/framework/wpf/advanced/dependency-properties-overview)  
  
-   [Sistema de layout](/dotnet/framework/wpf/advanced/layout)  
  
-   [Estilos e modelos](/dotnet/framework/wpf/controls/styles-and-templates)  
  
Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:  
  
-   [Visão geral do desenvolvimento de aplicativos](/dotnet/framework/wpf/app-development/index)  
  
-   [Visão geral dos controles](/dotnet/framework/wpf/controls/index)  
  
-   [Visão geral da vinculação de dados](/dotnet/framework/wpf/data/data-binding-overview)  
  
-   [Visão geral de mídia, animação e elementos gráficos do WPF](/dotnet/framework/wpf/graphics-multimedia/index)  
  
-   [Documentos no WPF](/dotnet/framework/wpf/advanced/documents-in-wpf)  
  
## <a name="see-also"></a>Consulte também

[Criar modernos aplicativos da área de trabalho com o Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
