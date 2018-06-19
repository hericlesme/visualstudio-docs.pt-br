---
title: Criar um ambiente de desenvolvimento do .NET Core com contêineres usando o Kubernetes na nuvem com o Visual Studio – Etapa 5 – Chamar outro contêiner | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: ab3934e6f7f013dd21309dc8c98461983bdfe30a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898421"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introdução ao Connected Environment com .NET Core e Visual Studio

Etapa anterior: [Depurar um contêiner no Kubernetes](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>Chamar outro contêiner
Nesta seção, vamos criar um segundo serviço, o `mywebapi` e fazer com que o `webfrontend` o chame. Cada serviço será executado em um contêiner separado. Em seguida, vamos depurar nos dois contêineres.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Baixe o exemplo de código da *mywebapi*
Por motivo de tempo, vamos baixar o código de exemplo de um repositório do GitHub. Acesse https://github.com/Azure/vsce e selecione **Clonar ou Baixar** para baixar o repositório do GitHub. O código para essa seção está em `vsce/samples/dotnetcore/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Executar a *mywebapi*
1. Abra o projeto `mywebapi` em uma *janela separada do Visual Studio*.
1. Selecione **Connected Environment para AKS** na lista suspensa de configurações de inicialização, como você fez anteriormente para o projeto `webfrontend`. Em vez de criar um novo ambiente de desenvolvimento, selecione o mesmo que você já criou. Assim como antes, deixe o espaço como o padrão `mainline` e clique em **OK**. Na janela de Saída, você poderá perceber que o Visual Studio começa a "preparar” esse novo serviço no ambiente de desenvolvimento para acelerar as coisas quando você iniciar a depuração.
1. Pressione F5 e espere que o serviço seja criado e implantado. Você saberá que ele está pronto quando a barra de status do Visual Studio ficar laranja
1. Anote a URL do ponto de extremidade exibida no painel **Connected Environment para AKS** na janela **Saída**. Ela será parecida com http://localhost:\<portnumber\>. Pode parecer que o contêiner está sendo executado localmente, mas, na verdade, ele está sendo executado no nosso ambiente de desenvolvimento no Azure.
1. Quando a `mywebapi` estiver pronta, abra o navegador no endereço do localhost e acrescente `/api/values` à URL para invocar a API GET padrão para o `ValuesController`. 
1. Se todas as etapas foram bem-sucedidas, será exibida uma resposta do serviço `mywebapi` semelhante a esta.

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Fazer uma solicitação do *webfrontend* para a *mywebapi*
Agora, vamos escrever o código agora no `webfrontend` que faz uma solicitação para a `mywebapi`. Mude para a janela do Visual Studio que tem o projeto `webfrontend`. No arquivo `HomeController.cs`, *substitua* o código do método Sobre pelo seguinte:

 ```csharp
    public async Task<IActionResult> About()
    {
        ViewData["Message"] = "Hello from webfrontend";
        
        // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
        // headers in the incoming request to any outgoing requests
        using (var client = new HeaderPropagatingHttpClient(this.Request))
        {
            // Call *mywebapi*, and display its response in the page
            var response = await client.GetAsync("http://mywebapi/api/values/1");
            ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
        }
    
        return View();
    }

```

Observe como a descoberta de serviço DNS do Kubernetes é usada para referir-se ao serviço como `http://mywebapi`. **O código no ambiente de desenvolvimento está sendo executado da mesma forma em que será executado em produção**.

O exemplo de código acima também usa uma classe `HeaderPropagatingHttpClient`. Esta classe auxiliar é o arquivo `HeaderPropagation.cs` que foi adicionado ao projeto quando você o configurou para usar um Connected Environment. `HeaderPropagatingHttpClient` é derivado da conhecida classe `HttpClient` e adiciona a funcionalidade de propagar cabeçalhos específicos de um objeto HttpRequest do ASP .NET existente para um objeto HttpRequestMessage de saída. Mais adiante, você verá como isso facilita uma experiência de desenvolvimento mais produtiva em cenários de equipe.

## <a name="debug-across-multiple-services"></a>Depurar entre vários serviços
1. Neste ponto, a `mywebapi` ainda deve estar sendo executada com o depurador anexado. Se ela não estiver, pressione F5 no projeto `mywebapi`.
1. Defina um ponto de interrupção no método `Get(int id)` no arquivo `ValuesController.cs` que manipula as solicitações GET `api/values/{id}`.
1. No projeto `webfrontend`, no qual colamos o código acima, defina um ponto de interrupção antes do ponto em que ele envia uma solicitação GET para `mywebapi/api/values`.
1. Pressione F5 no projeto `webfrontend`. O Visual Studio abrirá novamente um navegador para a porta do localhost apropriada e o aplicativo Web será exibido.
1. Clique no link "**Sobre**" na parte superior da página para disparar o ponto de interrupção no projeto `webfrontend`. 
1. Pressione F10 para continuar. O ponto de interrupção do projeto `mywebapi` será disparado agora.
1. Pressione F5 para continuar e você retornará ao código no projeto `webfrontend`.
1. Pressionar F5 mais uma vez concluirá a solicitação e retornará uma página no navegador. No aplicativo Web, a página Sobre exibirá uma mensagem concatenada pelos dois serviços: "Olá do webfrontend e Olá da mywebapi".

Muito bem! Agora você tem um aplicativo com vários contêineres e cada contêiner pode ser desenvolvido e implantado separadamente.

> [!div class="nextstepaction"]
> [Saiba mais sobre o desenvolvimento em equipe](get-started-netcore-visualstudio-06.md)

