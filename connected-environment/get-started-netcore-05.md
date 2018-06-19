---
title: Criar um ambiente de desenvolvimento do .NET Core com contêineres usando o Kubernetes na nuvem – Etapa 5 – Chamar outro contêiner | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: 6ef3a79d0b79feae64adcaebe31daa48ba75ab75
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31887330"
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introdução ao Connected Environment com .NET Core

Etapa anterior: [Depurar um contêiner no Kubernetes](get-started-netcore-04.md)

Nesta seção, vamos criar um segundo serviço, o `mywebapi` e fazer com que o `webfrontend` o chame. Cada serviço será executado em um contêiner separado. Em seguida, vamos depurar nos dois contêineres.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Baixe o exemplo de código da *mywebapi*
Por motivo de tempo, vamos baixar o código de exemplo de um repositório do GitHub. Acesse https://github.com/Azure/vsce e selecione **Clonar ou Baixar** para baixar o repositório do GitHub. O código para essa seção está em `vsce/samples/dotnetcore/getting-started/mywebapi`.


## <a name="run-mywebapi"></a>Executar a *mywebapi*
1. Abra a pasta `mywebapi` em uma *janela do VS Code separada*.
1. Pressione F5 e espere que o serviço seja criado e implantado. Você saberá que ele está pronto quando a barra de depuração do VS Code aparecer.
1. Anote a URL do ponto de extremidade, ela será parecida com http://localhost:\<portnumber\>. **Dica: a barra de status do VS Code exibirá uma URL clicável.** Pode parecer que o contêiner está sendo executado localmente, mas, na verdade, ele está sendo executado no nosso ambiente de desenvolvimento no Azure. O motivo para o endereço do localhost é que a `mywebapi` não definiu nenhum ponto de extremidade público e somente pode ser acessada por meio da instância do Kubernetes. Para sua conveniência e para facilitar a interação com o serviço privado em seu computador local, o Connected Environment cria um túnel SSH temporário para o contêiner em execução no Azure.
1. Quando a `mywebapi` estiver pronta, abra o navegador no endereço do localhost. Acrescente `/api/values` à URL para invocar a API GET padrão para o `ValuesController`. 
1. Se todas as etapas foram bem-sucedidas, será exibida uma resposta do serviço `mywebapi`.


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Fazer uma solicitação do *webfrontend* para a *mywebapi*
Agora, vamos escrever o código agora no `webfrontend` que faz uma solicitação para a `mywebapi`.
1. Mude para a janela do VS Code do `webfrontend`.
1. *Substitua* o código do método Sobre:

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

O exemplo de código acima também usa uma classe `HeaderPropagatingHttpClient`. Essa classe auxiliar foi adicionada à pasta do código quando `vsce init` foi executado. `HeaderPropagatingHttpClient` é derivado da conhecida classe `HttpClient` e adiciona a funcionalidade de propagar cabeçalhos específicos de um objeto HttpRequest do ASP .NET existente para um objeto HttpRequestMessage de saída. Mais adiante, você verá como isso facilita uma experiência de desenvolvimento mais produtiva em cenários de equipe.


## <a name="debug-across-multiple-services"></a>Depurar entre vários serviços
1. Neste ponto, a `mywebapi` ainda deve estar sendo executada com o depurador anexado. Se ela não estiver, pressione F5 no projeto `mywebapi`.
1. Defina um ponto de interrupção no método `Get(int id)` que manipula as solicitações GET `api/values/{id}`.
1. No projeto `webfrontend`, defina um ponto de interrupção antes do ponto em que ele envia uma solicitação GET para `mywebapi/api/values`.
1. Pressione F5 no projeto `webfrontend`.
1. Invoque o aplicativo Web e percorra o código nos dois serviços.
1. No aplicativo Web, a página Sobre exibirá uma mensagem concatenada pelos dois serviços: "Olá do webfrontend e Olá da mywebapi".


Muito bem! Agora você tem um aplicativo com vários contêineres e cada contêiner pode ser desenvolvido e implantado separadamente.

> [!div class="nextstepaction"]
> [Saiba mais sobre o desenvolvimento em equipe](get-started-netcore-06.md)

