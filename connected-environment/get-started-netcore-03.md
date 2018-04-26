---
title: 'Criar um ambiente de desenvolvimento do .NET Core com contêineres usando o Kubernetes na nuvem – Etapa 3: Criar um aplicativo Web ASP.NET Core | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: 72c7df0a82b91f7b4665b8b7e2cecdfc2eea26cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introdução ao Connected Environment com .NET Core

Etapa anterior: [Criar um ambiente de desenvolvimento do Kubernetes no Azure](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>Criar um aplicativo Web do ASP.NET Core
Se o [.NET Core](https://www.microsoft.com/net) estiver instalado, você poderá criar rapidamente um aplicativo Web ASP.NET Core em uma pasta chamada `webfrontend`.
```cmd
dotnet new mvc --name webfrontend
```

Como alternativa, **baixe o código de exemplo do GitHub** navegando até https://github.com/Azure/vsce e selecionando **Clonar ou Baixar** para baixar o repositório do GitHub em seu ambiente local. O código para este guia está em `vsce/samples/dotnetcore/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Atualizar um arquivo de conteúdo
O Connected Environment não se trata apenas de executar o código no Kubernetes, mas também de permitir que você veja rapidamente e iterativamente as alterações no código entrarem em vigor em um ambiente do Kubernetes na nuvem.

1. Localize o arquivo `./Views/Home/Index.cshtml` e faça uma edição no HTML. Por exemplo, altere a linha 70 que diz `<h2>Application uses</h2>` para algo como: `<h2>Hello k8s in Azure!</h2>`
1. Salve o arquivo. Um pouco depois, na janela do terminal, aparecerá uma mensagem informando que um arquivo no contêiner em execução foi atualizado.
1. Acesse o navegador e atualize a página. A página da Web deverá exibir o HTML atualizado.

O que aconteceu? As edições em arquivos de conteúdo, como HTML e CSS, não exigem recompilação em um aplicativo Web .NET Core, portanto, um comando `vsce up` ativo sincronizará automaticamente os arquivos de conteúdo modificados no contêiner em execução no Azure, oferecendo uma maneira rápida de exibir as edições de conteúdo.

## <a name="update-a-code-file"></a>Atualizar um arquivo de código
A atualização dos arquivos de código requer um pouco mais de trabalho porque o aplicativo .NET Core precisa ser recompilado e produzir os binários do aplicativo atualizados.

1. Na janela do terminal, pressione `Ctrl+C` (para parar o `vsce up`).
1. Abra o arquivo de código chamado `Controllers/HomeController.cs`e edite a mensagem que a página Sobre exibirá: `ViewData["Message"] = "Your application description page.";`
1. Salve o arquivo.
1. Execute `vsce up` na janela do terminal. 

Isso recria a imagem de contêiner e reimplanta o gráfico do Helm. Para ver as alterações do código entrarem em vigor no aplicativo em execução, acesse o menu Sobre no aplicativo Web.


Mas existe um *método ainda mais rápido* para o desenvolvimento de código, que vamos explorar na próxima seção. 
> [!div class="nextstepaction"]
> [Depurar um contêiner no Kubernetes](get-started-netcore-04.md)

