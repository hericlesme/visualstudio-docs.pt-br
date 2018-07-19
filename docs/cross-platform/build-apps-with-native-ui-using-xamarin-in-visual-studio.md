---
title: Compilar aplicativos com interface do usuário nativa usando Xamarin no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 1b70ea2cc12530065b2a297e54ff494bcc765c9c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757247"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Criar aplicativos com interface do usuário nativa usando o Xamarin no Visual Studio

A maioria dos desenvolvedores que escolhem o Xamarin e C# para escrever aplicativos móveis multiplataforma usam o Xamarin.Forms. O Xamarin.Forms define uma interface do usuário que é mapeada para controles nativos no iOS, no Android e na UWP (Plataforma Universal do Windows). O Xamarin.Forms é descrito no artigo [Aprenda as noções básicas de criação de aplicativos com o Xamarin.Forms no Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

Este artigo descreve uma abordagem diferente que envolve acessar as APIs nativas da interface do usuário de cada plataforma. Trabalhar com as APIs nativas é uma abordagem muito mais difícil do que o Xamarin.Forms porque requer bastante conhecimento de cada plataforma. A vantagem é que você pode personalizar a interface do usuário de acordo com os recursos e pontos fortes específicos de cada plataforma e ainda compartilhar a lógica de negócios.

Depois de concluir as etapas em [Instalar e configurar](../cross-platform/setup-and-install.md) e em [Verificar seu ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md), este passo a passo mostrará como criar um aplicativo Xamarin básico com camadas da interface do usuário nativa. Com a interface do usuário nativa, o código compartilhado reside em uma biblioteca do .NET Standard e os projetos de plataforma individuais contêm as definições da interface do usuário. Aqui está o aplicativo que você criará, em execução nos telefones iOS, Android e Windows 10 Desktop (da esquerda para a direita).

![Aplicativo Xamarin no iOS, Android e Windows](../cross-platform/media/cross-plat-xamarin-build-1-Large.png#lightbox)

Você executará as seguintes ações para compilar:

- [Configurar sua solução](#solution)

- [Escrever código de serviço de dados compartilhado](#dataservice)

- [Projetar a interface do usuário para Android](#Android)

- [Projetar a interface do usuário para Windows](#Windows)

- [Próximas etapas](#next), que incluem a criação de uma interface do usuário do iOS

> [!TIP]
> Você pode encontrar o código-fonte completo para esse projeto no [repositório de amostras móveis no GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Se você tiver dificuldades ou encontrar erros, publique perguntas em [forums.xamarin.com](http://forums.xamarin.com). Muitos erros podem ser resolvidos atualizando para os SDKs mais recentes exigidos pelo Xamarin, que são descritos nas [Notas de Versão do Xamarin](https://developer.xamarin.com/releases/) de cada plataforma.

> [!NOTE]
> A documentação do desenvolvedor do Xamarin também oferece várias instruções passo a passo com seções de Início Rápido e de Aprofundamento conforme listado abaixo. Em todas essas páginas, verifique se "Visual Studio" está selecionado para ver as instruções passo a passo específicas do Visual Studio.
>
>  -   Aplicativos Xamarin com interface do usuário nativa:
>     -   [Olá, Android](/xamarin/android/get-started/hello-android/) (aplicativo simples com uma tela)
>     -   [Olá, Android multitela](/xamarin/android/get-started/hello-android-multiscreen/) (aplicativo com navegação entre telas)
>     -   [Passo a passo de fragmentos do Android](/xamarin/android/platform/fragments/implementing-with-fragments/) (usado para telas mestre/detalhadas, entre outros elementos)
>     -   [Hello, iOS](/xamarin/ios/get-started/hello-iOS/)
>     -   [Multitela Hello, iOS](/xamarin/ios/get-started/hello-iOS-multiscreen/)

>  -   Aplicativos Xamarin com Xamarin.Forms (interface do usuário compartilhada)
>     -   [Hello, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart/)
>     -   [Multitela Hello, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms-multiscreen/)

<a name="solution" />

##  <a name="set-up-your-solution"></a>Configurar sua solução

O Visual Studio não tem um modelo de solução para criar aplicativos nativos da interface do usuário compartilhando uma biblioteca do .NET Standard. No entanto, não é difícil criar uma solução dessas por meio dos projetos individuais. Essas etapas criam uma solução do Xamarin com projetos para cada tipo de plataforma do aplicativo e uma biblioteca do .NET Standard para código compartilhado.

1.  No Visual Studio, crie uma nova solução de **Biblioteca de Classes (.NET Standard)** e nomeie-a como **WeatherApp**. É mais fácil encontrar esse modelo selecionando **Visual C#** à esquerda e, em seguida, **.NET Standard**:

    ![Criando a solução .NET Standard](../cross-platform/media/cross-plat-xamarin-build-2.png)

    Depois de clicar em OK, a solução **WeatherApp** consiste em um único projeto chamado **WeatherApp**.

2.  Se você desejar direcionar ao iOS, adicione um projeto do iOS à solução. Clique com botão direito do mouse no nome da solução no **Gerenciador de Soluções**, selecione **Adicionar** e **Novo Projeto**.  Na caixa de diálogo **Novo Projeto**, à esquerda, selecione **Visual C#** e, em seguida, **iOS** e **Universal**. (Se ele não estiver lá, poderá ser necessário instalar o Xamarin ou habilitar o recurso do Visual Studio 2017, confira [Instalar e configurar](../cross-platform/setup-and-install.md).) Na lista de modelos, selecione **Aplicativo de Exibição Única (iOS)**. Nomeie-o como **WeatherApp.iOS**.

3.  Se você desejar direcionar ao Android, adicione um projeto do Android à solução. Na caixa de diálogo **Novo Projeto** à esquerda, selecione **Visual C#** e **Android**. Na lista de modelos, selecione **Aplicativo em Branco (Android)**. Nomeie-o como **WeatherApp.Android**.

4. Se você desejar direcionar à Plataforma Universal do Windows, na caixa de diálogo **Novo Projeto** à esquerda, selecione **Visual C#** e **Universal do Windows**. Na lista de modelos, selecione **Aplicativo em Branco (Universal do Windows)** e nomeie-o como **WeatherApp.UWP**.

5. Para cada um dos projetos de aplicativo (iOS, Android e UWP), clique com o botão direito do mouse na seção **Referências** no **Gerenciador de Soluções** e selecione **Adicionar Referência**. Na caixa de diálogo **Gerenciador de Referências** à esquerda, selecione **Projeto** e **Solução**. Será exibida uma lista de todos os projetos na solução, exceto o projeto cujas referências você está gerenciando:

   ![Definindo uma referência para o projeto .NET Standard](../cross-platform/media/cross-plat-xamarin-build-3.png)

   Marque a caixa de seleção ao lado de **WeatherApp**.

   Depois que você marcar esta caixa para cada um dos projetos de aplicativo, todos os projetos conterão referências à biblioteca .NET Standard e poderão compartilhar o código nessa biblioteca.

6. Adicione o pacote NuGet **Newtonsoft.Json** ao projeto do .NET Standard, que você usará para processar as informações recuperadas de um serviço de dados de clima:

    -   Clique com o botão direito do mouse no projeto **WeatherApp** no **Gerenciador de Soluções** e selecione **Gerenciar pacotes NuGet...**.

         Na janela do NuGet, selecione a guia **Procurar** e pesquise **Newtonsoft**.

    -   Selecione **Newtonsoft.Json**.

    -   Verifique se o campo **Versão** está definido como a versão **Estável mais recente**.

    -   Clique em **Instalar**.

7.  Repita a Etapa 6 para localizar e instalar o pacote **Microsoft.CSharp** no projeto do .NET Standard. Essa biblioteca é necessária para usar o tipo de dados `dynamic` do C# em uma biblioteca do .NET Standard.

8.  Compile sua solução e verifique não se há erros de build.

<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Escrever código de serviço de dados compartilhados

 O projeto **WeatherApp** é a biblioteca do .NET Standard. É neste projeto que você escreverá o código que será compartilhado entre todas as plataformas. Como cada projeto de aplicativo tem uma referência à biblioteca do .NET Standard, a biblioteca é incluída com os pacotes dos aplicativos iOS, Android e UWP.

 As etapas a seguir adicionam os códigos à biblioteca do .NET Standard para acessar e armazenar dados desse serviço de clima:

1.  Primeiro inscreva-se para obter uma chave de API de clima gratuita em [http://openweathermap.org/appid](http://openweathermap.org/appid). Esta chave de API permite que o aplicativo obtenha o clima de qualquer código postal dos Estados Unidos. (Ela não funciona para códigos postais fora dos Estados Unidos.)

2.  Clique com botão direito do mouse no projeto **WeatherApp** e selecione **Adicionar > Classe…**. Na caixa de diálogo **Adicionar Novo Item**, dê ao arquivo o nome **Weather.cs**. Você usará essa classe para armazenar dados do serviço de dados de clima.

3.  Substitua todo o conteúdo de **Weather.cs** pelo código a seguir:

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

4.  Adicione outra classe ao projeto do .NET Standard chamada **DataService.cs**. Você usará essa classe para processar dados JSON do serviço de dados de clima.

5.  Substitua todo o conteúdo de **DataService.cs** pelo código a seguir:

    ```csharp
    using System.Net.Http;
    using System.Threading.Tasks;
    using Newtonsoft.Json;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> GetDataFromService(string queryString)
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

6.  Adicione uma terceira classe à biblioteca do .NET Standard chamada **Core.cs**. Você usará essa classe para formar uma cadeia de consulta com um código postal, chamar o serviço de dados de clima e popular uma instância da classe **clima**.

7.  Substitua o conteúdo do **Core.cs** pelo código a seguir:

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

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.GetDataFromService(queryString).ConfigureAwait(false);

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

8. Substitua a primeira ocorrência de *SUA CHAVE DE API AQUI* pela chave de API que você obteve na Etapa 1. Ela ainda precisa de aspas.

9. Exclua **MyClass.cs** da biblioteca .NET Standard porque ela não será usada.

10. Compile o projeto **WeatherApp** para garantir que o código esteja correto.

<a name="Android" />

## <a name="design-ui-for-android"></a>Projetar a interface do usuário para Android

 Agora você pode projetar a interface do usuário, conectá-la ao código compartilhado e, em seguida, executar o aplicativo.

### <a name="design-the-look-and-feel-of-your-app"></a>Criar a aparência de seu aplicativo

1.  No **Gerenciador de Soluções**, expanda a pasta **WeatherApp.Droid > Recursos > layout** e abra **Main.axml**. Esse comando abre o arquivo no Designer Visual. (Se for exibido um erro relacionado a Java, consulte esta [postagem de blog](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    >  Há muitos outros arquivos no projeto. Eles não serão explorados neste tópico, mas se você quiser se aprofundar um pouco mais na estrutura de um projeto Android, veja a [Parte 2: aprofundamento](/xamarin/android/get-started/hello-android/hello-android-deepdive/) do artigo Hello, Android.

2.  Abra a Caixa de Ferramentas com **Exibir > Outras Janelas > Caixa de Ferramentas**.

3.  Em **Caixa de Ferramentas**, arraste um controle **RelativeLayout** para o designer. Você usará esse controle como um contêiner pai para outros controles.

    > [!TIP]
    >  Se, a qualquer momento, o layout parecer não ser exibido corretamente, salve o arquivo e troque entre as guias **Design** e **Fonte** para atualizar.

4.  Na janela **Propriedades**, defina a propriedade **tela de fundo** (no grupo Estilo) como `#545454`.  Verifique pelo título na janela **Propriedades** se você está definindo a tela de fundo para o **RelativeLayout**.

5.  Na **Caixa de Ferramentas**, arraste um controle **TextView** para o controle **RelativeLayout**.

6.  Na janela **Propriedades**, defina estas propriedades. (Pode ajudar classificar a lista em ordem alfabética usando o botão de classificação na barra de ferramentas da janela Propriedades):

    |Propriedade|Valor|
    |--------------|-----------|
    |**text**|**Pesquisar por CEP**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginStart**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**textStyle**|`bold`|

    > [!TIP]
    >  Observe que muitas propriedades não contêm uma lista suspensa de valores que você pode selecionar.  Pode ser difícil adivinhar qual valor de cadeia de caracteres usar para qualquer propriedade específica. Para obter sugestões, tente pesquisar o nome de uma propriedade na página [R.attr](http://developer.android.com/reference/android/R.attr.html).
    >
    >  Além disso, uma pesquisa rápida na Web geralmente leva a uma página no [http://stackoverflow.com/](http://stackoverflow.com/) na qual outras pessoas já usaram a mesma propriedade.

     Para referência, se você mudar para a exibição **Fonte**, deverá ver o seguinte código para esse elemento:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_marginStart="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

7.  Na **Caixa de Ferramentas**, arraste um controle **TextView** para o controle **RelativeLayout** e posicione-o abaixo do controle ZipCodeSearchLabel. Descarte o novo controle na borda apropriada do controle existente. Isso ajuda a aumentar um pouco o zoom no designer para posicionar o controle.

8. Na janela **Propriedades**, defina estas propriedades:

    |Propriedade|Valor|
    |--------------|-----------|
    |**text**|**Código Postal**|
    |**id**|`@+id/ZipCodeLabel`|
    |**layout_marginStart**|`10dp`|
    |**layout_marginTop**|`6dp`|
    |**textColor**|`@android:color/white`|

    É assim que o código na exibição **Códgio-fonte** deverá estar:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginStart="10dp"
        android:layout_marginTop="6dp"
        android:textColor="@android:color/white" />
    ```

9. Na **Caixa de Ferramentas**, arraste um controle de **Número** para **RelativeLayout** e posicione-o abaixo do rótulo **CEP**. Então defina as propriedades a seguir:

    |Propriedade|Valor|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginStart**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**width**|`165dp`|
    |**textColor**|`@android:color/white`|

    O controle de **Número** é onde o usuário digita um código postal de cinco dígitos dos Estados Unidos. Aqui está a marcação que corresponde a esse controle:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginStart="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp"
        android:textColor="@android:color/white" />
    ```

10. Na **Caixa de Ferramentas**, arraste um **Botão** para o controle **RelativeLayout** e posicione-o à direita do controle zipCodeEntry. Então defina estas propriedades:

    |Propriedade|Valor|
    |--------------|-----------|
    |**id**|`@+id/weatherBtn`|
    |**text**|**Get Weather**|
    |**layout_marginStart**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**width**|`165dp`|

    ```xml
    <Button
        android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginStart="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

11. Agora você já tem conhecimento suficiente para criar uma interface do usuário básica usando o designer do Android. Você também pode criar uma interface do usuário adicionando a marcação diretamente no arquivo Main.axml da página. Para criar o restante da interface do usuário dessa forma, mude para a exibição Código-fonte no designer e, em seguida, cole a seguinte marcação *abaixo* da marca de fim `</RelativeLayout>`. (Ela deve estar abaixo da marca porque esses elementos *não* estão contidos no `RelativeLayout`.)

    ```xml
    <TextView
        android:text="Location"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/locationLabel"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/locationText"
        android:layout_marginStart="20dp"
        android:layout_marginBottom="10dp" />
    <TextView
        android:text="Temperature"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/tempLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/tempText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Wind Speed"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/windLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/windText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Humidity"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/humidtyLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/humidityText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Visibility"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/visibilityLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/visibilityText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Time of Sunrise"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunriseLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunriseText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Time of Sunset"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunsetLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunsetText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    ```

12. Salve o arquivo e mude para o modo de exibição de **Design**. Sua interface do usuário deve aparecer da seguinte maneira:

     ![Interface do usuário para aplicativo Android](../cross-platform/media/xamarin_androidui.png)

13. Abra **MainActivity.cs**. Veja como o código deve estar:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

14. Compile o projeto Android para verificar seu trabalho. O processo de build adiciona IDs de controle nos arquivos **Resource.Designer.cs** para que seja possível referenciar os controles por nome no código.

### <a name="consume-your-shared-code"></a>Consumir seu código compartilhado

1.  Abra o arquivo **MainActivity.cs** do projeto **WeatherApp** no editor de código e substitua seu conteúdo pelo código a seguir. Esse código chama o método `GetWeather` que você definiu no seu código compartilhado. Em seguida, na interface do usuário do aplicativo, ele mostra os dados recuperados daquele método.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App",
                  Theme = "@android:style/Theme.Material.Light",
                  MainLauncher = true)]
        public class MainActivity : Activity
        {
            protected override void OnCreate(Bundle bundle)
            {
                base.OnCreate(bundle);

                SetContentView(Resource.Layout.Main);

                Button button = FindViewById<Button>(Resource.Id.weatherBtn);

                button.Click += Button_Click;
            }

            private async void Button_Click(object sender, EventArgs e)
            {
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);

                if (!String.IsNullOrEmpty(zipCodeEntry.Text))
                {
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;
                }
            }
        }
    }
    ```

    Observe que a atividade recebeu um tema de tela de fundo clara.

### <a name="run-the-app-and-see-how-it-looks"></a>Execute o aplicativo e veja a aparência dele

1.  Em **Gerenciador de Soluções**, garanta que o projeto **WeatherApp.Droid** esteja definido como o projeto de inicialização.

2.  Selecione um destino de emulador ou dispositivo apropriado e inicie o aplicativo pressionando a tecla F5.

    > [!NOTE]
    > Se o Visual Studio indicar que o projeto Android não consegue localizar o arquivo Newtonsoft.Json, adicione esse pacote NuGet ao projeto Android.

3.  No dispositivo ou no emulador, digite um código postal de cinco dígitos válido dos Estados Unidos na caixa de edição e pressione **Obter Clima**. Dados de clima para aquela região então são exibidos nos controles.

    [![Aplicativo Xamarin no Android](../cross-platform/media/cross-plat-xamarin-build-1-android.png)](../cross-platform/media/cross-plat-xamarin-build-1-android-Large.png#lightbox)

> [!TIP]
>  O código-fonte completo para esse projeto está no [repositório de amostras móveis no GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

<a name="Windows" />

## <a name="design-ui-for-windows"></a>Projetar a interface do usuário para Windows

A próxima etapa é projetar a interface do usuário do Windows, conectá-la ao código compartilhado e, em seguida, executar o aplicativo.

### <a name="design-the-look-and-feel-of-your-app"></a>Criar a aparência de seu aplicativo

 O processo de criação de uma interface do usuário nativa da UWP em um aplicativo Xamarin não é diferente de nenhum outro aplicativo nativo da UWP. Por esse motivo, o uso do designer não será discutido aqui. Para obter uma discussão detalhada, confira [Criando uma interface de usuário usando o Designer XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 Nesse caso, abra **MainPage.xaml** e substitua todo o conteúdo XAML pela seguinte marcação:

```xaml
<Page
    x:Class="WeatherApp.UWP.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.UWP"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel HorizontalAlignment="Left"
                    VerticalAlignment="Top"
                    Height="40" Margin="10,0,0,0" Width="400">
            <TextBlock Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left"
                    VerticalAlignment="Top"
                    Height="120" Margin="10,40,0,0" Width="400"
                    Background="#FF545454">

            <TextBlock Text="Search by Zip Code" TextWrapping="Wrap"
                       HorizontalAlignment="Left" Margin="10,10,0,0"
                       Foreground="White" FontSize="18" FontWeight="Bold" />

            <TextBlock Text="Zip Code" TextWrapping="Wrap"
                       Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>

            <StackPanel Orientation="Horizontal">

                <TextBox x:Name="zipCodeEntry" Text=""
                         Margin="10,10,0,0" VerticalAlignment="Top"
                         InputScope="Number" Width="165" />

                <Button x:Name="weatherBtn" Content="Get Weather"
                        Foreground="White" Width="165" Margin="20,0,0,0" Height="60"
                        Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>

        <StackPanel Margin="10,175,0,0">
            <StackPanel.Resources>
                <Style x:Key="commonText" TargetType="TextBlock">
                    <Setter Property="HorizontalAlignment" Value="Left" />
                    <Setter Property="VerticalAlignment" Value="Top" />
                    <Setter Property="TextWrapping" Value="Wrap" />
                </Style>

                <Style x:Key="labelText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="14" />
                    <Setter Property="Foreground" Value="#FFA8A8A8" />
                </Style>

                <Style x:Key="valueText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="18" />
                    <Setter Property="Margin" Value="10, 0, 0, 10" />
                </Style>
            </StackPanel.Resources>

            <TextBlock Text="Location" Style="{StaticResource labelText}" />
            <TextBlock x:Name="locationText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="tempText" Style="{StaticResource valueText}" />

            <TextBlock Text="Wind Speed" Style="{StaticResource labelText}" />
            <TextBlock x:Name="windText" Style="{StaticResource valueText}" />

            <TextBlock Text="Humidity" Style="{StaticResource labelText}" />
            <TextBlock x:Name="humidityText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="visibilityText" Style="{StaticResource valueText}" />

            <TextBlock Text="Time of Sunrise" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunriseText" Style="{StaticResource valueText}" />

            <TextBlock Text="Time of Sunset" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunsetText" Style="{StaticResource valueText}" />
        </StackPanel>
    </Grid>
</Page>
```

### <a name="consume-your-shared-code"></a>Consumir seu código compartilhado

No arquivo code-behind **MainPage.xaml.cs**, adicione o seguinte manipulador de eventos para o botão:

```csharp
private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)
{
    if (!String.IsNullOrEmpty(zipCodeEntry.Text))
    {
        Weather weather = await Core.GetWeather(zipCodeEntry.Text);
        locationText.Text = weather.Title;
        tempText.Text = weather.Temperature;
        windText.Text = weather.Wind;
        visibilityText.Text = weather.Visibility;
        humidityText.Text = weather.Humidity;
        sunriseText.Text = weather.Sunrise;
        sunsetText.Text = weather.Sunset;

        weatherBtn.Content = "Search Again";
    }
}
```

Esse código chama o método `GetWeather` que você definiu no seu código compartilhado. `GetWeather` é o mesmo método que foi chamado no aplicativo Android. Esse código também mostra os dados recuperados do método nos controles da interface do usuário do seu aplicativo.

### <a name="run-the-app-and-see-how-it-looks"></a>Execute o aplicativo e veja a aparência dele

1.  No **Gerenciador de Soluções**, defina o projeto **WeatherApp.UWP** como o projeto de inicialização.

2.  Na caixa suspensa **Plataformas da Solução**, selecione **x86** e selecione **Computador Local** para implantar o aplicativo no Windows 10 Desktop.

3.  Inicie o aplicativo pressionando a tecla F5.

4.  Digite um código postal de cinco dígitos válido dos Estados Unidos na caixa de edição e pressione **Obter Clima**. Em seguida, os dados de clima dessa região serão exibidos na página.

    [![Aplicativo Xamarin no UWP](../cross-platform/media/cross-plat-xamarin-build-1-uwp.png)](../cross-platform/media/cross-plat-xamarin-build-1-uwp-Large.png#lightbox)

> [!TIP]
>  O código-fonte completo para esse projeto está no [repositório de amostras móveis no GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

<a name="next" />

## <a name="next-steps"></a>Próximas etapas

 **Adicionar a interface do usuário para iOS à solução**

 Estenda este exemplo adicionando a interface do usuário nativa para iOS. Para testar o código no iOS, você precisará se conectar a um Mac na rede local que tenha o Xcode e o Xamarin instalados. Depois de fazer isso, você poderá usar o designer do iOS diretamente no Visual Studio. Consulte o [repositório de amostras móveis no GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) para um aplicativo completo.

 Confira também o passo a passo [Hello, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?tabs=vswin).

 **Adicionar código específico da plataforma em um projeto compartilhado**

 O código compartilhado em uma biblioteca do .NET Standard é neutro em relação à plataforma. A biblioteca é compilada uma única vez e incluída em cada pacote do aplicativo específico da plataforma. Se você quiser escrever código compartilhado que use compilação condicional para isolar o código específico da plataforma, poderá usar um projeto *compartilhado*. Para obter mais informações, confira [Opções de compartilhamento de código](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies).

## <a name="see-also"></a>Consulte também

- [Documentação do Xamarin](http://docs.microsoft.com/xamarin)
- [Centro de Desenvolvedores do Windows](https://dev.windows.com/en-us)
- [Pôster de referência rápida de Swift e C#](http://aka.ms/scposter)
