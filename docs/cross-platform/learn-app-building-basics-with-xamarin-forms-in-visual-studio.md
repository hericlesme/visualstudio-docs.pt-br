---
title: Noções básicas de compilação de aplicativos com o Xamarin.Forms no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 608eebc113c9df7a8978299cc69907e28d81a16f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Aprender as noções básicas de criação de aplicativos com o Xamarin.Forms no Visual Studio

Depois de concluir as etapas em [Instalar e configurar](../cross-platform/setup-and-install.md) e em [Verificar seu ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md), este passo a passo mostrará como criar um aplicativo básico com o Xamarin.Forms. Com o Xamarin.Forms, você escreverá todo o código da interface do usuário uma única vez em uma biblioteca de classes .NET Standard. Em seguida, o Xamarin renderizará automaticamente os controles de interface do usuário nativos para as plataformas iOS, Android e Plataforma Universal do Windows. 

É melhor usar uma biblioteca do .NET Standard em vez de um projeto compartilhado para este código comum. A biblioteca do .NET Standard inclui as APIs do .NET que podem ser executadas em todas as plataformas de destino.  

Aqui está o aplicativo que você criará. Ele está em execução (da esquerda para a direita) em telefones iOS e Android e na UWP (Plataforma Universal do Windows) do Windows 10:
  
[![O exemplo de aplicativo de clima no iOS, Android e UWP](../cross-platform/media/crossplat-xamarin-formsguide-1.png "FormsGuide 1 do Xamarin CrossPlat")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)
  
Você executará estas etapas para criar esse aplicativo:  
  
-   [Configurar sua solução](#solution)  
  
-   [Escrever código de serviço de dados compartilhado](#dataservice)  
  
-   [Começar a escrever código de interface do usuário compartilhado](#uicode)  
  
-   [Testar seu aplicativo usando o Emulador do Visual Studio para Android](#test)  
  
-   [Concluir a interface do usuário com uma aparência nativa entre plataformas](#finish)  
  
> [!TIP]
> Você pode encontrar o código-fonte completo desse projeto no [repositório xamarin-forms-samples no GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
<a name="solution" />

## <a name="set-up-your-solution"></a>Configurar sua solução  

Estas etapas criam uma solução do Xamarin.Forms que contém uma biblioteca de classes .Net Standard para o código compartilhado e dois pacotes NuGet adicionados. 
  
1. No Visual Studio, crie uma nova solução de **Aplicativo de Plataforma Cruzada (Xamarin.Forms)** e dê a ela o nome de **WeatherApp**. Procure o modelo selecionando **Visual C#** e **Plataforma Cruzada** na lista à esquerda.  
    
    ![Criando um novo projeto de aplicativo do Xamarin.Forms multiplataforma](../cross-platform/media/crossplat-xamarin-formsguide-2.png "FormsGuide 2 do Xamarin CrossPlat")

    Se o modelo não estiver lá, poderá ser necessário instalar o Xamarin ou habilitar o recurso do Visual Studio 2017. Confira [Instalar e configurar](../cross-platform/setup-and-install.md).  

2.  Depois de clicar em OK, você terá a oportunidade de selecionar algumas opções. Escolha **Aplicativo em Branco** e **.NET Standard**:

    ![Criar um novo projeto de Aplicativo de Plataforma Cruzada](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  Depois de clicar em OK para criar a solução, você terá uma solução com quatro projetos:  
  
    -   **WeatherApp**: a biblioteca .NET Standard na qual você escreverá o código compartilhado entre plataformas, incluindo lógica de negócios comum e código de interface do usuário usando Xamarin.Forms.  
  
    -   **WeatherApp.Android**: o projeto que contém o código nativo do Android.  
  
    -   **WeatherApp.iOS**: o projeto que contém o código iOS nativo.  
  
    -   **WeatherApp.UWP**: o projeto que contém o código da UWP do Windows 10.  
  
    > [!NOTE]
    >  Você tem a liberdade de excluir qualquer um dos projetos que for relativo a uma plataforma que não for de seu interesse.   
  
     Dentro de cada projeto nativo, você tem acesso ao designer nativo da plataforma correspondente e pode implementar telas e funcionalidades específicas da plataforma, conforme o necessário.  
  
4.  Atualize o pacote NuGet do Xamarin.Forms em sua solução para a versão estável mais recente da seguinte maneira:  
  
    -   Selecione **Ferramentas > Gerenciador de Pacotes do NuGet > Gerenciar Pacotes do NuGet para a Solução**.  
  
    -   Na guia **Atualizações**, marque o pacote **Xamarin.Forms** e marque para atualizar todos os projetos em sua solução. (Não selecione as atualizações das bibliotecas de suporte do Xamarin Android.)  
  
    -   Atualize o campo **Versão** para a versão **Estável mais recente** disponível.  
  
    -   Clique em **Instalar**.  
  
         ![Atualizando o pacote do NuGet do Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  

    Você deve adquirir o hábito de atualizar a versão do Xamarin.Forms sempre que criar uma nova solução do Xamarin.Forms. Não atualize nenhuma biblioteca de suporte do Android. Se necessário, essas bibliotecas serão atualizadas quando você atualizar a versão do Xamarin.Forms.
  
5.  Adicione o pacote NuGet **Newtonsoft.Json** no projeto **WeatherApp**. Essa biblioteca é usada para processar as informações recuperadas de um serviço de dados de clima:  
  
    -   No Gerenciador de Pacotes do NuGet (aberto desde a etapa 4), selecione a guia **Procurar** e pesquise **Newtonsoft**.  
  
    -   Selecione **Newtonsoft.Json**.  
  
    -   Marque o projeto **WeatherApp**, que é o único projeto no qual você precisa instalar o pacote.  
  
    -   Verifique se o campo **Versão** está definido como a versão **Estável mais recente**.  
  
    -   Clique em **Instalar**.  
  
    ![Localizando e instalando o pacote do NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  Repita a Etapa 5 para localizar e instalar o pacote **Microsoft.CSharp** no projeto do .NET Standard. Essa biblioteca é necessária para usar o tipo de dados `dynamic` do C# em uma biblioteca do .NET Standard.
  
7.  Compile sua solução e verifique não se há erros de build.  
  
<a name="dataservice" /> 

## <a name="write-shared-data-service-code"></a>Escrever código de serviço de dados compartilhados  

É no projeto de biblioteca **WeatherApp** do .NET Standard que você escreverá o código que será compartilhado entre todas as plataformas. Essa biblioteca é referenciada pelos pacotes do aplicativo criados pelos projetos iOS, Android e Windows.  
  
Para executar este exemplo, primeiro você precisa se inscrever para obter uma chave de API gratuita em [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
Depois, as etapas a seguir adicionam o código à biblioteca .NET Standard para acessar e armazenar dados do serviço meteorológico:  
  
1.  Clique com botão direito do mouse no projeto **WeatherApp** e selecione **Adicionar > Classe…**. Na caixa de diálogo **Adicionar Novo Item**, dê ao arquivo o nome **Weather.cs**. Você usará essa classe para armazenar dados do serviço de dados de clima.  
  
2.  Substitua todo o conteúdo de **Weather.cs** pelo código a seguir:  
  
    ```csharp  
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```  
  
3.  Adicione outra classe ao projeto **WeatherApp** chamada **DataService.cs** que você usará para processar dados JSON do serviço de dados meteorológicos.  
  
4.  Substitua todo o conteúdo de **DataService.cs** pelo código a seguir:  
  
    ```csharp  
    using System.Net.Http;  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
    
    namespace WeatherApp  
    {  
        public class DataService  
        {  
            public static async Task<dynamic> getDataFromService(string queryString)  
            {  
                HttpClient client = new HttpClient();  
                var response = await client.GetAsync(queryString);  
  
                dynamic data = null;  
                if (response != null)  
                {  
                    string json = response.Content.ReadAsStringAsync().Result;  
                    data = JsonConvert.DeserializeObject(json);  
                }  
  
                return data;  
            }  
        }  
    }  
    ```  
  
5.  Adicione uma classe de terceiros ao projeto **WeatherApp** chamado **Core.cs** no qual você colocará a lógica de negócios compartilhada. Esse código forma uma cadeia de consulta com um código postal, chama o serviço de dados de clima e popula uma instância da classe `Weather`.  
  
6.  Substitua o conteúdo do **Core.cs** pelo código a seguir:  
  
    ```csharp  
    using System;  
    using System.Threading.Tasks;  
  
    namespace WeatherApp  
    {  
        public class Core  
        {  
            public static async Task<Weather> GetWeather(string zipCode)  
            {  
                //Sign up for a free API key at http://openweathermap.org/appid  
                string key = "YOUR API KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  
  
                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);  
  
                if (results["weather"] != null)  
                {  
                    Weather weather = new Weather();  
                    weather.Title = (string)results["name"];                  
                    weather.Temperature = (string)results["main"]["temp"] + " F";  
                    weather.Wind = (string)results["wind"]["speed"] + " mph";                  
                    weather.Humidity = (string)results["main"]["humidity"] + " %";  
                    weather.Visibility = (string)results["weather"][0]["main"];  
  
                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);  
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);  
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);  
                    weather.Sunrise = sunrise.ToString() + " UTC";  
                    weather.Sunset = sunset.ToString() + " UTC";  
                    return weather;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
        }  
    }  
    ```  

7. Substitua *SUA CHAVE DE API AQUI* pela chave de API que você obteve. Ela ainda precisa de aspas.     
  
8.  Compile o projeto de biblioteca **WeatherApp** para garantir que o código esteja correto.  
  
 <a name="uicode" /> 

## <a name="begin-writing-shared-ui-code"></a>Começar a escrever o código da interface do usuário compartilhado  

O Xamarin.Forms permite implementar o código da interface do usuário compartilhado na biblioteca do .NET Standard. Nessas etapas, você adicionará uma página ao projeto com um botão. Esse botão atualiza o texto na página com os dados retornados pelo serviço de clima que você viu na seção anterior:  
  
1.  Adicione uma **Página de Conteúdo** chamada **WeatherPage** clicando com o botão direito do mouse no projeto **WeatherApp** e selecionando **Adicionar > Novo Item...** . Na caixa de diálogo **Adicionar Novo Item**, selecione **Página de Conteúdo**. Tenha cuidado para não selecionar **Página de Conteúdo (C#)** ou **Exibição de Conteúdo**. Nomeie-a como **WeatherPage.xaml**.  
  
    ![Adicionando uma nova página XAML do Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     O Xamarin.Forms é baseado em XAML, de forma que esta etapa cria um arquivo **WeatherPage.xaml** em conjunto com o arquivo code-behind aninhado **WeatherPage.xaml.cs**. Você pode escrever a lógica da interface do usuário em XAML ou em código. Você fará um pouco de cada um neste passo a passo.  
  
2.  Para adicionar um botão à tela **WeatherPage**, substitua o conteúdo de **WeatherPage.xaml** pela seguinte marcação:  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">  
      <Button x:Name="getWeatherBtn" 
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />  
    </ContentPage>  
    ```  
  
     Observe que o nome do botão precisa ser definido usando o atributo `x:Name` para que seja possível referenciar esse botão por nome de dentro do arquivo code-behind.  
  
3.  Para adicionar um manipulador de eventos ao evento `Clicked` do botão para atualizar o texto do botão, substitua o conteúdo de **WeatherPage.xaml.cs** pelo código a seguir. (Fique à vontade para trocar "60601" por outro código postal.)  
  
    ```csharp  
    using System;  
    using Xamarin.Forms;  
  
    namespace WeatherApp  
    {  
        public partial class WeatherPage: ContentPage  
        {  
            public WeatherPage()  
            {  
                InitializeComponent();  
  
                //Set the default binding to a default object for now  
                BindingContext = new Weather();  
            }  
  
            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
            {  
                Weather weather = await Core.GetWeather("60601");  
                getWeatherBtn.Text = weather.Title;  
            }  
        }  
    }  
    ```  
  
4.  Para abrir **WeatherPage** como a primeira tela quando o aplicativo for iniciado, substitua o construtor padrão em **App.xaml.cs** pelo código a seguir:  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Compile o projeto **WeatherApp** para garantir que o código esteja correto.  
  
<a name="test" /> 

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a>Testar o aplicativo usando o Emulador do Visual Studio para Android  

Agora está tudo pronto para executar o aplicativo! Vamos executar apenas a versão para Android por enquanto para verificar se o aplicativo está obtendo dados do serviço de clima. Mais tarde, você também executará as versões para iOS e UWP, depois de adicionar mais elementos da interface do usuário.   
  
1.  Defina o projeto **WeatherApp.Android** como o projeto de inicialização clicando com o botão direito do mouse e selecionando **Definir como Projeto de Inicialização**.  
  
2.  Na barra de ferramentas do Visual Studio, você verá **WeatherApp.Android** listado como o projeto de destino. Selecione um dos emuladores do Android para depuração e pressione **F5**. Recomendamos o uso de uma das opções de emulador do **Visual Studio** que executará o aplicativo no Emulador do Visual Studio para Android.  
  
    ![Selecionar um destino de depuração do Emulador do Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

    > [!NOTE]
    > Se o Visual Studio indicar que o projeto Android não consegue localizar o arquivo Newtonsoft.Json, adicione esse pacote NuGet ao projeto Android.   
  
3.  Quando o aplicativo for iniciado no emulador, clique no botão **Get Weather** (Obter clima). O texto do botão deverá ser atualizado para **Chicago**, que é a propriedade `Title` dos dados recuperados do serviço de tempo.  
  
     ![Aplicativo meteorológico antes e depois de pressionar o botão](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  

<a name="finish" /> 

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a>Concluir a interface do usuário com uma aparência nativa entre as plataformas  

O Xamarin.Forms renderiza controles nativos da interface do usuário para cada plataforma, para que seu aplicativo tenha uma aparência nativa automaticamente. Você poderá ver essa aparência nativa com mais clareza ao terminar a interface do usuário, incluindo um campo de entrada para um código postal e controles para exibir dados de tempo.  
  
1.  Substitua o conteúdo de **WeatherPage.xaml** pela marcação abaixo. Os elementos nomeados por meio do atributo `x:Name`, conforme já descrito, podem ser referenciados no código. O Xamarin.Forms também fornece algumas [opções de layout](/xamarin/xamarin-forms/controls/layouts/). Aqui, o WeatherPage está usando [Grade](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) e [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/).  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
            
                <Label Text="Search by Zip Code" 
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />
            
                <Label x:Name="zipCodeLabel" Text="Zip Code:" 
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />
            
                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />
            
                <Button x:Name="getWeatherBtn" Text="Get Weather" 
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>  
     ```  
  
     Embora não seja mostrado aqui, você pode usar a marca `OnPlatform` em arquivos XAML para selecionar um valor da propriedade específico da plataforma atual na qual o aplicativo está em execução (confira [Sintaxe XAML essencial](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax/).) No arquivo code-behind, você pode determinar em qual plataforma o aplicativo é executado comparando a propriedade [`Device.RuntimePlatform`](https://developer.xamarin.com/api/property/Xamarin.Forms.Device.RuntimePlatform/) com as constantes definidas na classe [`Device`](https://developer.xamarin.com/api/type/Xamarin.Forms.Device/) denominada [`Device.iOS`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.iOS/), [`Device.Android`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.Android/) e [`Device.UWP`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.UWP/).  
  
2.  Em **WeatherPage.xaml.cs**, substitua o manipulador de eventos `GetWeatherBtn_Clicked` pelo código a seguir. Esse código verifica se há um código postal no campo de entrada e recupera os dados referentes a esse código postal. Em seguida, define o contexto de associação da página inteira para a instância de `Weather` resultante. O código é concluído, definindo o texto do botão como "Pesquisar Novamente". Cada rótulo na interface do usuário é associado a uma propriedade da classe `Weather`. Quando você define o contexto de associação da tela para uma instância de `Weather`, os rótulos são atualizados automaticamente.  
  
    ```csharp  
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
    {  
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
        {  
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
            BindingContext = weather;  
            getWeatherBtn.Text = "Search Again";  
        }  
    }  
    ```  
  
3.  Execute o aplicativo nas três plataformas, clicando com o botão direito do mouse no projeto apropriado, selecionando **Definir como projeto de inicialização** e iniciando o aplicativo em um dispositivo ou emulador. Insira um código postal válido dos Estados Unidos com cinco dígitos e pressione o botão **Obter Clima** para exibir os dados de clima dessa região. O Visual Studio precisará estar conectado a um computador Mac na rede para o projeto do iOS.  
  
     [![O exemplo de aplicativo de clima no iOS, Android e UWP](../cross-platform/media/crossplat-xamarin-formsguide-1.png "FormsGuide 1 do Xamarin CrossPlat")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)
  
O código-fonte completo desse projeto no [repositório xamarin-forms-samples no GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).