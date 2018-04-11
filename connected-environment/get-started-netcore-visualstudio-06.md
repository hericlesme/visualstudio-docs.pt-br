---
title: Criar um ambiente de desenvolvimento .NET Core com contêineres usando o Kubernetes na nuvem com o Visual Studio – Etapa 6 – Saiba mais sobre o desenvolvimento em equipe | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 04/05/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: d8d81afbe4fbf99c52107c8afc6f1eb9938de792
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introdução ao Connected Environment com .NET Core e Visual Studio

Etapa anterior: [Chamar outro contêiner](get-started-netcore-visualstudio-05.md)

## <a name="learn-about-team-development"></a>Saiba mais sobre o desenvolvimento em equipe

Até agora nós executamos o código do aplicativo como se fossemos o único desenvolvedor trabalhando no aplicativo. Nesta seção, aprenderemos como o Connected Environment simplifica o desenvolvimento em equipe:
* Habilite uma equipe de desenvolvedores para trabalhar no mesmo ambiente de desenvolvimento.
* Há suporte para cada desenvolvedor iterar em seu código isoladamente e sem medo de interromper outras pessoas.
* Teste o código de ponta a ponta antes de confirmá-lo, sem precisar criar códigos fictícios nem simular dependências.

## <a name="challenges-with-developing-microservices"></a>Desafios do desenvolvimento de microsserviços
Nosso aplicativo de exemplo não está muito complexo no momento. Mas no desenvolvimento real, os desafios logo surgem à medida que mais serviços são adicionados e que a equipe de desenvolvimento aumenta.

Imagine-se trabalhando em um serviço que interage com dezenas de outros serviços.

1. Executar todos os itens de desenvolvimento localmente pode ser algo irrealista. Sua máquina de desenvolvimento pode não ter recursos suficientes para executar o aplicativo inteiro. Ou, talvez seu aplicativo tenha pontos de extremidade que precisem estar acessíveis publicamente (por exemplo, se seu aplicativo responde a um webhook de um aplicativo de SaaS).
1. Você pode tentar executar somente os serviços dos quais depende, mas isso significa que você precisaria saber o fechamento completo das dependências (por exemplo, as dependências das dependências). Ou, a questão é que não é fácil saber como compilar e executar as dependências porque não foi você que trabalhou nelas.
1. Alguns desenvolvedores recorrerem à simulação ou à criação de fictícios de muitas das dependências do serviço. Isso pode ajudar às vezes, mas o gerenciamento dessas simulações logo pode exigir seu próprio esforço de desenvolvimento. Além disso, isso resulta em um ambiente de desenvolvimento muito diferente do ambiente de produção e erros sutis podem surgir.
1. A conclusão é que fica muito difícil fazer qualquer tipo de teste de ponta a ponta. Os testes de integração podem ocorrer de forma realista somente após a confirmação, o que significa que podem ocorrer problemas posteriormente no ciclo de desenvolvimento.

    ![](media/microservices-challenges.png)

## <a name="work-in-a-shared-development-environment"></a>Trabalhar em um ambiente de desenvolvimento compartilhado
Com o Connected Environment, você pode configurar um ambiente de desenvolvimento *compartilhado* no Azure. Cada desenvolvedor pode se concentrar apenas em sua parte do aplicativo e pode desenvolver iterativamente *um código de pré-confirmação* em um ambiente que já contém todos os outros serviços e recursos de nuvem dos quais seus cenários dependem. As dependências estão sempre atualizadas e os desenvolvedores trabalham de uma forma que reflete a produção.

## <a name="work-in-your-own-space"></a>Trabalhar em seu próprio espaço
À medida que você desenvolve o código do serviço e antes que ele esteja pronto para o check-in, geralmente ele não fica em um estado bom. Você ainda está formatando, testando e experimentando co código com as soluções de forma iterativa. O Connected Environment oferece o conceito de **espaço**, que permite trabalhar isoladamente e sem medo de interromper os membros da equipe.

Faça o seguinte para garantir que os dois serviços, `webfrontend` e `mywebapi`, estejam em execução em nosso ambiente de desenvolvimento **e no espaço `mainline`**.
1. Feche todas as sessões de F5/depuração dos dois serviços, mas mantenha os projetos abertos em suas janelas do Visual Studio.
2. Mude para a janela do Visual Studio com o projeto `mywebapi` e pressione Ctrl + F5 para executar o serviço sem o depurador anexado
3. Mude para a janela do Visual Studio com o projeto `webfrontend` e pressione Ctrl + F5 para executá-lo também.

> [!Note]
Às vezes, é necessário atualizar o navegador depois que a página da Web é exibida pela primeira vez após um Ctrl + F5.

Qualquer pessoa que abrir a URL pública e navegar para o aplicativo Web invocará o caminho do código que nós já gravamos, que é executado por meio dos dois serviços usando o espaço `mainline` padrão. Agora vamos supor que queremos continuar a desenvolver a `mywebapi`. Como podemos fazer isso sem interromper os outros desenvolvedores que estão usando o ambiente de desenvolvimento? Para fazer isso, configuraremos nosso próprio espaço.

### <a name="create-a-new-space"></a>Criar um novo espaço
De dentro do Visual Studio você pode criar espaços adicionais que serão usados quando você pressionar F5 ou Ctrl + F5 para o serviço. Você pode nomear o espaço como desejar e ser flexível sobre seu significado (por exemplo, `sprint4` ou `demo`).

Faça o seguinte para criar um novo espaço:
1. Mude para a janela do Visual Studio com o projeto `mywebapi`.
2. Clique com botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Propriedades**.
3. Selecione a guia **Depurar** à esquerda para mostrar as configurações do Connected Environment.
4. Aqui você pode alterar ou criar o Connected Environment e/ou o espaço que será usado ao pressionar F5 ou Ctrl + F5. *Verifique se o Connected Environment que você criou anteriormente está selecionado*.
5. Na lista suspensa **Espaço** selecione **<Criar novo espaço...>**.

    ![](images/Settings.png)

6. Na caixa de diálogo **Adicionar Espaço** digite um nome para o espaço e clique em **OK**. Eu usei meu nome ("scott") para o novo espaço para que meus colegas pudessem identificar que este é o espaço no qual estou trabalhando.

    ![](images/AddSpace.png)

7. Agora você verá seu ambiente de desenvolvimento e o novo Espaço selecionado na página de propriedades do projeto.

    ![](images/Settings2.png)

### <a name="update-code-for-mywebapi"></a>Atualizar o código da *mywebapi*

1. No projeto `mywebapi` faça uma alteração no código para o método `string Get(int id)` no arquivo `ValuesController.cs` da seguinte maneira:
 
    ```csharp
    [HttpGet("{id}")]
    public string Get(int id)
    {
        return "mywebapi now says something new";
    }
    ```

2. Defina um ponto de interrupção neste bloco de código atualizado (talvez já exista um que foi definido antes).
3. Pressione F5 para iniciar o serviço `mywebapi`. Essa ação iniciará o serviço em seu ambiente de desenvolvimento usando o espaço selecionado, que no meu caso é o `scott`.

Aqui está um diagrama que o ajudará a entender como funcionam os diferentes espaços. O caminho azul mostra uma solicitação por meio do espaço `mainline`, que é o caminho padrão usado quando não é acrescentado nenhum espaço à URL. O caminho verde mostra uma solicitação por meio do espaço `scott`.

![](media/Space-Routing.png)

Essa capacidade interna do Connected Environment permite testar o código de ponta a ponta em um ambiente compartilhado, sem precisar que cada desenvolvedor recrie a pilha completa de serviços em seu espaço. Observe que este roteamento exige que cabeçalhos de propagação sejam encaminhados no código do aplicativo, conforme foi ilustrado na etapa anterior deste guia.

## <a name="test-code-running-in-the-scott-space"></a>Testar o código em execução no espaço `scott`
Para testar a nova versão da `mywebapi` em conjunto com o `webfrontend`, abra o navegador na URL de ponto de acesso público do `webfrontend` (por exemplo, https://webfrontend-teamenv.vsce.io) e acesse a página Sobre. A mensagem original "Olá do webfrontend e Olá da mywebapi" deverá ser exibida.

Agora, adicione a parte "scott-" à URL da seguinte forma: https://scott-webfrontend-teamenv.vsce.io e atualize o navegador. O ponto de interrupção definido no projeto `mywebapi` deverá ser atingido. Clique em F5 para continuar e em seu navegador, agora deverá ser exibida a nova mensagem "Olá do webfrontend e da mywebapi” dizendo algo novo. O motivo é que o caminho para o código atualizado na `mywebapi` está em execução no espaço `scott`.

> [!div class="nextstepaction"]
> [Resumo](get-started-netcore-visualstudio-07.md)