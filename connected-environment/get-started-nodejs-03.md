---
title: 'Criar um ambiente de desenvolvimento do Node.js com contêineres usando o Kubernetes na nuvem – Etapa 3: Criar um aplicativo Web ASP.NET | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: 34e1f07e173ccba6aab561fb4795abbe938e0127
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31890148"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introdução ao Connected Environment com Node.js

Etapa anterior: [Criar um ambiente de desenvolvimento do Kubernetes no Azure](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>Criar um aplicativo Web Node.js
Baixe o código do GitHub navegando para https://github.com/Azure/vsce e selecione **Clonar ou Baixar** para baixar o repositório do GitHub para seu ambiente local. O código para este guia está em `vsce/samples/nodejs/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Atualizar um arquivo de conteúdo
O Connected Environment não se trata apenas de executar o código no Kubernetes, mas também de permitir que você veja rapidamente e iterativamente as alterações no código entrarem em vigor em um ambiente do Kubernetes na nuvem.

1. Localize o arquivo `./public/index.html` e faça uma edição no HTML. Por exemplo, altere a cor da tela de fundo da página para uma sombra de azul:

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. Salve o arquivo. Um pouco depois, na janela do terminal, aparecerá uma mensagem informando que um arquivo no contêiner em execução foi atualizado.
1. Acesse o navegador e atualize a página. Você verá a atualização da cor.

O que aconteceu? As edições em arquivos de conteúdo, como HTML e CSS, não exigem que o processo do Node.js seja reiniciado, portanto, um comando `vsce up` ativo sincronizará automaticamente os arquivos de conteúdo modificados diretamente no contêiner em execução no Azure, oferecendo uma maneira rápida de exibir as edições de conteúdo.

### <a name="test-from-a-mobile-device"></a>Testar usando um dispositivo móvel
Se você abrir o aplicativo Web em um dispositivo móvel, verá que a interface do usuário não é exibida corretamente em um dispositivo pequeno.

Para corrigir isso, vamos adicionar uma marca META `viewport`:
1. Abra o arquivo `./public/index.html`
1. Adicione uma marca META `viewport` no elemento `head` existente:

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. Salve o arquivo.
1. Atualize o navegador do dispositivo. Agora o aplicativo Web será renderizado corretamente. 

Este é um exemplo de como alguns problemas realmente não são encontrados até que você teste nos dispositivos em que o aplicativo deve ser usado. Com o VS Connected Environment, você pode iterar no código e validar as alterações nos dispositivos de destino rapidamente.

## <a name="update-a-code-file"></a>Atualizar um arquivo de código
A atualização dos arquivos de código no servidor exige um pouco mais de trabalho, porque o aplicativo Node.js precisa ser reiniciado.

1. Na janela do terminal, pressione `Ctrl+C` (para parar o `vsce up`).
1. Abra o arquivo de código chamado `server.js` e edite a mensagem de saudação do serviço: 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. Salve o arquivo.
1. Execute `vsce up` na janela do terminal. 

Isso recria a imagem de contêiner e reimplanta o gráfico do Helm. Recarregue a página do navegador para ver as alterações no código entrarem em vigor.


Mas existe um *método ainda mais rápido* para o desenvolvimento de código, que vamos explorar na próxima seção. 
> [!div class="nextstepaction"]
> [Depurar um contêiner no Kubernetes](get-started-nodejs-04.md)
