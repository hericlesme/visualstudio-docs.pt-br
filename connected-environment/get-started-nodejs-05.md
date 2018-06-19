---
title: Criar um ambiente de desenvolvimento do Node.js com contêineres usando o Kubernetes na nuvem – Etapa 5 – Chamar outro contêiner | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: 89565869feec746aff75327b59ee7d0b466f26c1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31887499"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introdução ao Connected Environment com Node.js

Etapa anterior: [Depurar um contêiner no Kubernetes](get-started-nodejs-04.md)

Nesta seção, vamos criar um segundo serviço, o `mywebapi` e fazer com que o `webfrontend` o chame. Cada serviço será executado em um contêiner separado. Em seguida, vamos depurar nos dois contêineres.

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>Abra o código de exemplo da *mywebapi*
O código de exemplo da `mywebapi` para esse guia já deve estar em uma pasta chamada `vsce/samples` (caso contrário, acesse https://github.com/Azure/vsce e selecione **Clonar ou Baixar** para baixar o repositório do GitHub.) O código para essa seção está em `vsce/samples/nodejs/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Executar a *mywebapi*
1. Abra a pasta `mywebapi` em uma *janela do VS Code separada*.
1. Pressione F5 e espere que o serviço seja criado e implantado. Você saberá que ele está pronto quando a barra de depuração do VS Code aparecer.
1. Anote a URL do ponto de extremidade, ela será parecida com http://localhost:\<portnumber\>. **Dica: a barra de status do VS Code exibirá uma URL clicável.** Pode parecer que o contêiner está sendo executado localmente, mas, na verdade, ele está sendo executado no nosso ambiente de desenvolvimento no Azure. O motivo para o endereço do localhost é que a `mywebapi` não definiu nenhum ponto de extremidade público e somente pode ser acessada por meio da instância do Kubernetes. Para sua conveniência e para facilitar a interação com o serviço privado em seu computador local, o Connected Environment cria um túnel SSH temporário para o contêiner em execução no Azure.
1. Quando a `mywebapi` estiver pronta, abra o navegador no endereço do localhost. Uma resposta do serviço `mywebapi` deverá ser exibida ("Olá da mywebapi").


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Fazer uma solicitação do *webfrontend* para a *mywebapi*
Agora, vamos escrever o código agora no `webfrontend` que faz uma solicitação para a `mywebapi`.
1. Mude para a janela do VS Code do `webfrontend`.
1. Adicione estas linhas de código na parte superior do `server.js`:
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. *Substitua* o código do manipulador de GET `/api`. Ao lidar com uma solicitação, ele faz uma chamada para a `mywebapi` e, em seguida, retorna os resultados dos dois serviços.

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

Observe como a descoberta de serviço DNS do Kubernetes é usada para referir-se ao serviço como `http://mywebapi`. **O código no ambiente de desenvolvimento está sendo executado da mesma forma em que será executado em produção**.

O exemplo de código acima utiliza um módulo auxiliar chamado `propagateHeaders`. Este auxiliar foi adicionado à pasta do código quando `vsce init` foi executado. A função `propagateHeaders.from()` propaga cabeçalhos específicos de um objeto http.IncomingMessage existente em um objeto de cabeçalhos de uma solicitação de saída. Mais adiante, você verá como isso facilita uma experiência de desenvolvimento mais produtiva em cenários de equipe.


## <a name="debug-across-multiple-services"></a>Depurar entre vários serviços
1. Neste ponto, a `mywebapi` ainda deve estar sendo executada com o depurador anexado. Se ela não estiver, pressione F5 no projeto `mywebapi`.
1. Defina um ponto de interrupção no manipulador de GET `/` padrão.
1. No projeto `webfrontend`, defina um ponto de interrupção antes do ponto em que ele envia uma solicitação GET para `http://mywebapi`.
1. Pressione F5 no projeto `webfrontend`.
1. Abra o aplicativo Web e percorra o código nos dois serviços. O aplicativo Web deverá exibir uma mensagem concatenada pelos dois serviços: "Olá do webfrontend e Olá da mywebapi".


Muito bem! Agora você tem um aplicativo com vários contêineres e cada contêiner pode ser desenvolvido e implantado separadamente.

> [!div class="nextstepaction"]
> [Saiba mais sobre o desenvolvimento em equipe](get-started-nodejs-06.md)
