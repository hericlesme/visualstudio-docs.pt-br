---
title: Criar um ambiente de desenvolvimento Node.js com contêineres usando o Kubernetes na nuvem – Etapa 4 – Depurar um contêiner no Kubernetes | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: 8dca016f3a3feb2d1fb10a80695b82e531e48a74
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introdução ao Connected Environment com Node.js

Etapa anterior: [Criar um contêiner do Node.js no Kubernetes](get-started-nodejs-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Selecione a configuração de depuração do VSCE
1. Para abrir a exibição Depuração, clique no ícone de depuração na **Barra de Atividade** do lado do VS Code.
1. Selecione **Iniciar programa (VSCE)** como a configuração de depuração ativa.

![](media/debug-configuration-nodejs.png)

> [!Note]
> Se não houver nenhum comando do Connected Environment na paleta de comandos, verifique se a [extensão do VS Code para Connected Environment](get-started-nodejs-01.md#get-kubernetes-debugging-for-vs-code) foi instalada.

## <a name="debug-the-container-in-kubernetes"></a>Depurar o contêiner no Kubernetes
Pressione **F5** para depurar o código no Kubernetes!

Assim como acontece com o comando `up`, o código é sincronizado com o ambiente de desenvolvimento quando você inicia a depuração e um contêiner é criado e implantado no Kubernetes. Neste momento, o depurador é anexado ao contêiner remoto.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Defina um ponto de interrupção em um arquivo de código no servidor, por exemplo, em `app.get('/api'...` no `server.js`. Atualize a página do navegador ou pressione o botão 'Repita Isso' e você deverá atingir o ponto de interrupção e poderá percorrer o código.

Você tem acesso completo às informações de depuração exatamente como teria se o código tivesse sido executado localmente, como a pilha de chamadas, as variáveis locais, as informações de exceção, etc.

## <a name="edit-code-and-refresh-the-debug-session"></a>Editar o código e atualizar a sessão de depuração
Com o depurador ativo, faça uma edição no código. Por exemplo, modifique a mensagem de saudação novamente:

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

Salve o arquivo e, no **painel Ações de depuração**, clique no botão **Atualizar**. 

![](media/debug-action-refresh-nodejs.png)

Em vez de recompilar e reimplantar uma nova imagem de contêiner sempre que forem feitas edições no código, o que geralmente leva um tempo considerável, o Connected Environment reiniciará o processo do Node.js entre as sessões de depuração para fornecer um loop de edição/depuração mais rápido.

Atualize o aplicativo Web no navegador ou pressione o botão *Repita Isso*. Sua mensagem personalizada deverá ser exibida na interface do usuário.


## <a name="use-nodemon-to-develop-even-faster"></a>Usar o NodeMon para desenvolver com ainda mais rapidez
*Nodemon* é uma ferramenta popular que os desenvolvedores do Node.js usam para acelerar o desenvolvimento. Em vez de reiniciar manualmente o processo do Node sempre que é feita uma edição de código no servidor, os desenvolvedores geralmente configuram o projeto Node para que o *nodemon* monitore as alterações no arquivo e reinicie automaticamente o processo do servidor. Nesse estilo de trabalho, o desenvolvedor apenas atualiza seu navegador depois de fazer uma edição no código.

A intenção do Connected Environment é que você possa usar os mesmos fluxos de trabalho de desenvolvimento produtivos que você usa ao desenvolver localmente. Para ilustrar isso, o projeto de exemplo `webfrontend` foi configurado para usar o *nodemon* (ele é configurado como uma dependência de desenvolvimento em `package.json`).

Experimente o seguinte:
1. Pare o depurador do VS Code.
1. Clique no ícone de depuração na **Barra de Atividade** do lado do VS Code. 
1. Selecione **Anexar (VSCE)** como a configuração de depuração ativa.
1. Pressione F5.

Nessa configuração, o contêiner é configurado para iniciar o *nodemon*. Quando forem feitas edições de código no servidor, o *nodemon* reiniciará automaticamente o processo do Node, assim como ele faz quando você desenvolve localmente. 
1. Edite a mensagem de saudação novamente no `server.js` e salve o arquivo.
1. Atualize o navegador ou clique no botão *Repita Isso* para ver as alterações entrarem em vigor!

**Agora você tem um método para iterar no código rapidamente e depurar diretamente no Kubernetes!** Em seguida, veremos como é possível criar e chamar um segundo contêiner.

> [!div class="nextstepaction"]
> [Chamar um serviço em execução em um contêiner separado](get-started-nodejs-05.md)

