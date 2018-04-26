---
title: Solução de problemas | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: troubleshooting
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: b41d228bcced6149c95b09b2445dd656ed9772d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-guide"></a>Guia de solução de problemas

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>Erro 'erro ou desconexão/redefinição de conexão upstream antes de cabeçalhos'
Esse erro poderá ser exibido quando você tentar acessar o serviço. Por exemplo, ao acessar a URL do serviço em um navegador. 

**Motivo:** a porta do contêiner não está disponível. Estes são os motivos mais comuns: 
* O contêiner ainda está no processo de criação e implantação. Isso pode ocorrer quando você executa `vsce up` ou inicia o depurador e, em seguida, tenta acessar o contêiner antes que ele seja implantado com êxito.
* A configuração de porta não está consistente entre o Dockerfile, o gráfico do Helm e o código do servidor que abre uma porta.

**Tente o seguinte:**
1. Se o contêiner estiver no processo de criação/implantação, espere de 2 a 3 segundos e tente acessar o serviço novamente. 
1. Verifique a configuração de porta. Os números de porta especificados devem ser **idênticos** em todos os ativos abaixo:
    * **Dockerfile:** especificado pela instrução `EXPOSE`.
    * **[Gráfico do Helm](https://docs.helm.sh):** especificado pelos valores `externalPort` e `internalPort` de um serviço (geralmente localizado em um arquivo `values.yml`),
    * As portas abertas no código do aplicativo, por exemplo, no Node.js: `var server = app.listen(80, function () {...}`


## <a name="config-file-not-found"></a>Arquivo de configuração não encontrado
Você executa `vsce up` e obtém o seguinte erro: `Config file not found: .../vsce.yaml`

**Motivo:** `vsce up` precisa ser executado do diretório raiz do código que você deseja executar e a pasta de código precisa ter sido inicializada para ser executada com o Connected Environment.

**Tente o seguinte:**
1. Altere o diretório atual para a pasta raiz que contém o código do serviço. 
1. Se não houver um arquivo vsce.yaml na pasta de código, execute `vsce init` para gerar os ativos do Docker, do Kubernetes e do VSCE.

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>Erro: 'o programa de pipe 'vsce' foi encerrado inesperadamente com o código 126.'
Iniciar o depurador do VS Code, às vezes, pode resultar nesse erro. Isso é um bug.

**Tente o seguinte:**
1. Feche e abra o VS Code novamente.
2. Pressione F5 novamente.


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>Erro de depuração 'Não há suporte para o tipo de depuração 'coreclr' configurado'
A execução do depurador do VS Code relata o erro: `Configured debug type 'coreclr' is not supported.`

**Motivo:** você não tem a extensão do VS Code para o Connected Environment instalado no computador de desenvolvimento.

**Tente o seguinte:** instale a [extensão do VS Code para o Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>O portal do Azure não mostra as instâncias do Connected Environment

**Motivo:** ainda não há uma experiência do portal do Azure para o Connected Environment pronta para a versão prévia.


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>O tipo ou o nome do namespace 'MyLibrary' não pôde ser encontrado

**Motivo:** o contexto de build ocorre no nível do projeto ou do serviço por padrão, portanto, um projeto de biblioteca que você esteja usando não será localizado.

**Tente o seguinte:** o que precisa ser feito:
1. Modifique o arquivo vsce.yaml para definir o contexto de build para o nível da solução.
2. Modifique os arquivos Dockerfile e Dockerfile.develop para que eles se refiram corretamente aos arquivos csproj, em relação ao novo contexto de build.
3. Coloque um arquivo .dockerignore ao lado do arquivo .sln e modifique-o conforme o necessário.

Encontre um exemplo em https://github.com/sgreenmsft/buildcontextsample

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>Erro de autorização 'Microsoft.ConnectedEnvironment/registro/ação' ao criar um ambiente
O seguinte erro pode aparecer quando você está gerenciando um ambiente e está trabalhando em uma assinatura do Azure na qual não tem acesso de Proprietário ou Colaborador.
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**Motivo:** a assinatura do Azure selecionada não registrou o namespace Microsoft.ConnectedEnvironment.

**Tente o seguinte:** alguém com acesso de Proprietário ou Colaborador na assinatura do Azure pode executar o seguinte comando da CLI do Azure para registrar manualmente o namespace Microsoft.ConnectedEnvironment:

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>O VSCE parece não usar meu Dockerfile existente para criar um contêiner 

**Motivo:** o VSCE pode ser configurado para apontar para um Dockerfile específico em seu projeto. Se parecer que o VSCE não está usando o Dockerfile com o qual você pretende criar contêineres, poderá ser necessário informar o VSCE explicitamente onde ele está. 

**Tente o seguinte:** abra o arquivo `vsce.yaml` que foi gerado pelo VSCE em seu projeto. Use a diretiva `configurations->develop->build->dockerfile` para apontar para o Dockerfile que você deseja usar:

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```