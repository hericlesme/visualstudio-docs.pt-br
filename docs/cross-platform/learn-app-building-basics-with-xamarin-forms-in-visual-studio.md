---
title: Noções básicas de compilação de aplicativos com o Xamarin.Forms no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 6c0659e63feb685f002b7be969ee827e5e047cdd
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Aprender as noções básicas de criação de aplicativos com o Xamarin.Forms no Visual Studio

Após você concluir as etapas em [Configuração e instalação](../cross-platform/setup-and-install.md) e em [Verificar seu ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md), este passo a passo mostra como criar um aplicativo básico (mostrado abaixo) com Xamarin.Forms. Com o Xamarin.Forms, você escreverá todo o código da interface do usuário uma vez em uma biblioteca de classes .NET Standard. Em seguida, o Xamarin renderizará automaticamente os controles de interface do usuário nativos para as plataformas iOS, Android e Plataforma Universal do Windows. Recomendamos essa abordagem (em vez de um projeto compartilhado) porque a biblioteca .NET Standard inclui apenas as APIs do .NET que têm suporte em todas as plataformas de destino, e porque o Xamarin.Forms permite o compartilhamento do código da interface do usuário entre as plataformas.  
  
![O exemplo de aplicativo meteorológico em Android, iOS e Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
Você executará as seguintes ações para compilar:  
  
-   [Configurar sua solução](#solution)  
  
-   [Escrever código de serviço de dados compartilhado](#dataservice)  
  
-   [Começar a escrever código de interface do usuário compartilhado](#uicode)  
  
-   [Testar seu aplicativo usando o Emulador do Visual Studio para Android](#test)  
  
-   [Concluir a interface do usuário com uma aparência nativa entre plataformas](#finish)  
  
> [!TIP]
> Você pode encontrar o código-fonte completo desse projeto no [repositório xamarin-forms-samples no GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
##  <a name="solution"></a> Configurar sua solução  

Estas etapas criam uma solução do Xamarin.Forms que contém uma biblioteca de classes .Net Standard para o código compartilhado e dois pacotes NuGet adicionados.  
  
1.  No Visual Studio, crie uma nova solução de **Aplicativo de Plataforma Cruzada (Xamarin.Forms)** e dê a ela o nome de **WeatherApp**. Procure o modelo selecionando **Visual C#** e **Plataforma Cruzada** na lista à esquerda.  
  
     Se ele não estiver lá, talvez você precise instalar o Xamarin ou habilitar o recurso do Visual Studio 2017, confira [Configuração e instalação](../cross-platform/setup-and-install.md).  
  
     ![Criar um novo projeto de aplicativo em branco &#40;Aplicativo de Plataforma Cruzada do Xamarin.Forms&#41;](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Depois de clicar em OK, você terá a oportunidade de selecionar algumas opções. Escolha **Aplicativo em Branco**, **Xamarin.Forms** e **.NET Standard**:

     ![Criar um novo projeto de Aplicativo de Plataforma Cruzada](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  Depois de clicar em OK para criar a solução, você terá vários projetos individuais:  
  
    -   **WeatherApp**: a biblioteca .NET Standard na qual você escreverá o código compartilhado entre plataformas, incluindo lógica de negócios comum e código de interface do usuário usando Xamarin.Forms.  
  
    -   **WeatherApp.Android**: o projeto que contém o código nativo do Android. É definido como o projeto de inicialização padrão.  
  
    -   **WeatherApp.iOS**: o projeto que contém o código iOS nativo.  
  
    -   **WeatherApp.UWP**: o projeto que contém o código da UWP do Windows 10.  
  
    > [!NOTE]
    >  Você tem a liberdade de excluir qualquer um dos projetos que for relativo a uma plataforma que não for de seu interesse.   
  
     Dentro de cada projeto nativo, você tem acesso ao designer nativo da plataforma correspondente e pode implementar telas e funcionalidades específicas da plataforma, conforme necessário.  
  
4.  Atualize o pacote do NuGet do Xamarin.Forms em sua solução para a versão estável mais recente da seguinte maneira. Recomendamos faze isso sempre que você criar uma nova solução do Xamarin:  
  
    -   Selecione **Ferramentas > Gerenciador de Pacotes do NuGet > Gerenciar Pacotes do NuGet para a Solução**.  
  
    -   Na guia **Atualizações**, marque o pacote **Xamarin.Forms** e marque para atualizar todos os projetos em sua solução. (Observação: deixe atualizações de Xamarin.Android.Support desmarcadas.)  
  
    -   Atualize o campo **Versão** para a versão **Estável mais recente** disponível.  
  
    -   Clique em **Instalar**.  
  
         ![Atualizando o pacote do NuGet do Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
5.  Adicione os pacotes NuGet **Newtonsoft.Json** ao projeto **WeatherApp**, que você usará para processar as informações recuperadas de um serviço de dados meteorológicos:  
  
    -   No Gerenciador de Pacotes do NuGet (aberto desde a etapa 4), selecione a guia **Procurar** e pesquise **Newtonsoft**.  
  
    -   Selecione **Newtonsoft.Json**.  
  
    -   Marque o projeto **WeatherApp** (esse é o projeto único no qual você precisa instalar o pacote).  
  
    -   Verifique se o campo **Versão** está definido como a versão **Estável mais recente**.  
  
    -   Clique em **Instalar**.  
  
    ![Localizando e instalando o pacote do NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  Repita a etapa 5 para localizar e instalar o pacote **Microsoft.Net.Http**.  
  
7.  Compile sua solução e verifique não se há erros de build.  
  
##  <a name="dataservice"></a> Escrever código de serviço de dados compartilhados  

É no projeto **WeatherApp** que você escreverá código para a biblioteca .NET Standard que será compartilhada entre todas as plataformas. Essa biblioteca é incluída automaticamente nos pacotes de aplicativo compilados pelos projetos de iOS, Android e Windows.  
  
Para executar este exemplo, primeiro você precisa se inscrever para obter uma chave de API gratuita em [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
Depois, as etapas a seguir adicionam o código à biblioteca .NET Standard para acessar e armazenar dados do serviço meteorológico:  
  
1.  Clique com botão direito do mouse no projeto **WeatherApp** e selecione **Adicionar > Classe…**. Na caixa de diálogo **Adicionar Novo Item**, dê ao arquivo o nome **Weather.cs**. Você usará essa classe para armazenar dados do serviço de dados de clima.  
  
2.  Substitua todo o conteúdo de **Weather.cs** pelo seguinte:  
  
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
  
5.  Adicione uma terceira classe ao projeto **WeatherApp** chamada **Core**, na qual você colocará a lógica de negócios compartilhada. Esse código forma uma cadeia de consulta com um código postal, chama o serviço de dados meteorológicos e preenche uma instância da classe **Weather**.  
  
6.  Substitua o conteúdo de **Core.cs** pelo seguinte:  
  
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
                string key = "YOUR KEY HERE";  
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
  
7.  Compile o projeto de biblioteca **WeatherApp** para garantir que o código esteja correto.  
  
##  <a name="uicode"></a> Começar a escrever código de interface do usuário compartilhado  

O Xamarin.Forms permite que você implemente o código da interface do usuário compartilhado na biblioteca .NET Standard. Nessas etapas, você adicionará uma página ao projeto com um botão que atualiza seu texto com os dados retornados pelo código do serviço de dados meteorológicos adicionado na seção anterior:  
  
1.  Adicione uma **Página de Conteúdo** chamada **WeatherPage.cs** clicando com o botão direito no projeto **WeatherApp** e selecionando **Adicionar > Novo Item...**. Na caixa de diálogo **Adicionar Novo Item**, selecione **Página de Conteúdo**. Tenha cuidado para não selecionar **Página de Conteúdo (C#)** ou **Exibição de Conteúdo**. Dê a ela o nome **WeatherPage.cs**.  
  
     ![Adicionando uma nova página XAML do Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     O Xamarin.Forms é baseado em XAML, de forma que esta etapa cria um arquivo **WeatherPage.xaml** em conjunto com o arquivo code-behind aninhado **WeatherPage.xaml.cs**. Isso permite gerar a interface do usuário por meio de XAML ou código. Você fará um pouco de cada um neste passo a passo.  
  
2.  Para adicionar um botão à tela WeatherPage, substitua o conteúdo de **WeatherPage.xaml** pelo seguinte:  
  
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
  
     Observe que o nome do botão deve ser definido usando o atributo **x:Name** para que você possa fazer referência a esse botão pelo nome de dentro do arquivo code-behind.  
  
3.  Para adicionar um manipulador de eventos ao evento **Clicado** do botão para atualizar o texto do botão, substitua o conteúdo de **WeatherPage.xaml.cs** pelo código a seguir. (Fique à vontade para trocar "60601" por outro código postal.)  
  
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
  
4.  Para abrir **WeatherPage** como a primeira tela quando o aplicativo for iniciado, substitua o construtor padrão em **App.cs** pelo código a seguir:  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Compile o projeto **WeatherApp** para garantir que o código esteja correto.  
  
##  <a name="test"></a> Testar seu aplicativo usando o Emulador do Visual Studio para Android  

Agora está tudo pronto para executar o aplicativo! Vamos executar apenas a versão para Android por enquanto para verificar se o aplicativo está obtendo dados do serviço de clima. Mais tarde, você também executará as versões para iOS e UWP, depois de adicionar mais elementos da interface do usuário.   
  
1.  Defina o projeto **WeatherApp.Android** como o projeto de inicialização clicando com o botão direito do mouse e selecionando **Definir como Projeto de Inicialização**.  
  
2.  Na barra de ferramentas do Visual Studio, você verá **WeatherApp.Android** listado como o projeto de destino. Selecione um dos emuladores do Android para depuração e pressione **F5**. Recomendamos o uso de uma das opções de emulador do **Visual Studio** que executará o aplicativo no Emulador do Visual Studio para Android.  
  
     ![Selecionar um destino de depuração do Emulador do Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  Quando o aplicativo for iniciado no emulador, clique no botão **Get Weather** (Obter clima). Você verá o texto do botão atualizado para **Chicago**, que é a propriedade *Título* dos dados recuperados do serviço meteorológico.  
  
     ![Aplicativo meteorológico antes e depois de pressionar o botão](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a> Concluir a interface do usuário com uma aparência nativa entre plataformas  

O Xamarin.Forms renderiza controles nativos da interface do usuário para cada plataforma, para que seu aplicativo tenha uma aparência nativa automaticamente. Para ver isso mais claramente, vamos terminar a interface do usuário com um campo de entrada de código postal e, em seguida, exibir os dados de clima retornados do serviço.  
  
1.  Substitua o conteúdo de **WeatherPage.xaml** pelo código a seguir. Os elementos nomeados usando o atributo **x:Name**, conforme descrito anteriormente, podem ser referenciados no código. O Xamarin.Forms também fornece um número de [opções de layout](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com). Aqui, WeatherPage está usando [Grade](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) (xamarin.com) e [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).  
  
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
  
     Embora não seja exibido aqui, você pode usar a marca **OnPlatform** para selecionar um valor da propriedade específico à plataforma atual na qual o aplicativo está em execução (confira [Sintaxe XAML essencial](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (xamarin.com). No arquivo code-behind, você pode usar a [API Device.OnPlatform](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) para a mesma finalidade.  
  
2.  Em **WeatherPage.xaml.cs**, substitua manipulador de eventos **GetWeatherBtn_Clicked** pelo código a seguir. Esse código verifica se há um código postal no campo de entrada, recupera dados desse código postal, define o contexto de associação da página inteira como a instância resultante de **Weather** e define o texto do botão como "Pesquisar Novamente". Observe que cada rótulo na interface do usuário é associado a uma propriedade da classe **Weather**, para que ao definir o contexto de associação da tela para uma instância de **Weather**, os rótulos sejam atualizados automaticamente.  
  
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
  
3.  Execute o aplicativo nas três plataformas, iOS, Android e Windows, clicando com o botão direito do mouse no projeto apropriado, selecionando **Definir como projeto de inicialização** e iniciando o aplicativo em um dispositivo ou no emulador ou simulador. Insira um código postal válido dos Estados Unidos com cinco dígitos e pressione o botão **Get Weather** (Obter Clima) para exibir dados meteorológicos para essa região, conforme mostrado abaixo. Você precisará ter o Visual Studio conectado a um computador Mac OS X em sua rede para o projeto do iOS.  
  
     ![Exemplo de Aplicativo Meteorológico em iOS, Android e Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
O código-fonte completo desse projeto no [repositório xamarin-forms-samples no GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).