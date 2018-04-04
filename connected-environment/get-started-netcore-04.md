---
title: Criar um ambiente de desenvolvimento .NET Core com contêineres usando o Kubernetes na nuvem – Etapa 4 – Depurar um contêiner no Kubernetes | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: f06489194f70a3e7e617f4022917cd1d4a96337f
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introdução ao Connected Environment com .NET Core
 
Etapa anterior: [Criar um aplicativo Web ASP.NET Core](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Selecione a configuração de depuração do VSCE
1. Para abrir a exibição Depuração, clique no ícone de depuração na **Barra de Atividade** do lado do VS Code.
1. Selecione **Inicialização do .NET Core (VSCE)** como a configuração de depuração ativa.

![](media/debug-configuration.png)

> [!Note]
> Se não houver nenhum comando do Connected Environment na paleta de comandos, verifique se a [extensão do VS Code para Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code) foi instalada.


## <a name="debug-the-container-in-kubernetes"></a>Depurar o contêiner no Kubernetes
Pressione **F5** para depurar o código no Kubernetes.

Assim como acontece com o comando `up`, o código é sincronizado com o ambiente de desenvolvimento e um contêiner é criado e implantado no Kubernetes. Neste momento, o depurador é anexado ao contêiner remoto.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Defina um ponto de interrupção em um arquivo de código no servidor, por exemplo, na função `Index()` no arquivo de origem `Controllers/HomeController.cs`. Atualizar a página do navegador faz com que o ponto de interrupção seja atingido.

Você tem acesso completo às informações de depuração exatamente como teria se o código tivesse sido executado localmente, como a pilha de chamadas, as variáveis locais, as informações de exceção, etc.

## <a name="edit-code-and-refresh"></a>Edite o código e atualize
Com o depurador ativo, faça uma edição no código. Por exemplo, modifique a mensagem da página Sobre em `Controllers/HomeController.cs`. 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

Salve o arquivo e, no **painel Ações de depuração**, clique no botão **Atualizar**. 

![](media/debug-action-refresh.png)

Em vez de recompilar e reimplantar uma nova imagem de contêiner sempre que forem feitas edições no código, o que geralmente leva um tempo considerável, o Connected Environment recompilará o código de forma incremental dentro do contêiner existente para fornecer um loop de edição/depuração mais rápido.

Atualize o aplicativo Web no navegador e acesse a página Sobre. Sua mensagem personalizada deverá ser exibida na interface do usuário.

**Agora você tem um método para iterar no código rapidamente e depurar diretamente no Kubernetes!** Em seguida, veremos como é possível criar e chamar um segundo contêiner.

> [!div class="nextstepaction"]
> [Chamar um serviço em execução em um contêiner separado](get-started-netcore-05.md)
