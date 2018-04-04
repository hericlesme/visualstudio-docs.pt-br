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

![](../media/microservices-challenges.png)


## <a name="work-in-a-shared-development-environment"></a>Trabalhar em um ambiente de desenvolvimento compartilhado
Com o Connected Environment, você pode configurar um ambiente de desenvolvimento *compartilhado* no Azure. Cada desenvolvedor pode se concentrar apenas em sua parte do aplicativo e pode desenvolver iterativamente *um código de pré-confirmação* em um ambiente que já contém todos os outros serviços e recursos de nuvem dos quais seus cenários dependem. As dependências estão sempre atualizadas e os desenvolvedores trabalham de uma forma que reflete a produção.

## <a name="work-in-your-own-space"></a>Trabalhar em seu próprio espaço
À medida que você desenvolve o código do serviço e antes que ele esteja pronto para o check-in, geralmente ele não fica em um estado bom. Você ainda está formatando, testando e experimentando co código com as soluções de forma iterativa. O Connected Environment oferece o conceito de **espaço**, que permite trabalhar isoladamente e sem medo de interromper os membros da equipe.

> [!Note]
> Antes de continuar, feche todas as janelas do VS Code dos dois serviços e, em seguida, execute `vsce up -d` em cada uma das pastas raiz do serviço. (Essa é uma limitação da versão prévia).

Vamos examinar mais de perto onde os serviços estão sendo executados no momento. Execute o comando `vsce list` e você verá uma saída semelhante à seguinte:

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------------------
mywebapi     mainline  mywebapi-0.1.0     80/TCP  2m ago     <not attached>
webfrontend  mainline  webfrontend-0.1.0  80/TCP  1m ago     https://webfrontend-contosodev.vsce.io
```

A coluna Espaço mostra que os dois serviços estão em execução em um espaço chamado `mainline`. Qualquer pessoa que abrir a URL pública e navegar para o aplicativo Web invocará o caminho do código que nós já escrevemos, que é executado por meio dos dois serviços. Agora vamos supor que queremos continuar a desenvolver a `mywebapi`. Como podemos fazer isso e não interromper outros desenvolvedores que estejam usando o ambiente de desenvolvimento? Para fazer isso, configuraremos nosso próprio espaço.

## <a name="create-a-space"></a>Criar um espaço
Para executar nossa própria versão da `mywebapi` em um espaço que não seja o `mainline`, vamos criar nosso próprio espaço:
``` 
vsce space create --name scott
```

No exemplo acima, usei meu nome para o novo espaço para que meus colegas pudessem identificar que este é o espaço no qual estou trabalhando, mas você pode nomeá-lo como desejar e ser flexível sobre seu significado, como 'sprint4' ou 'demonstração'. 

Execute o comando `vsce space list` para exibir uma lista de todos os espaços no ambiente de desenvolvimento. Um asterisco (*) é exibido ao lado do espaço selecionado no momento. No nosso caso, o espaço chamado 'scott' foi selecionado automaticamente quando foi criado. Você pode selecionar outro espaço a qualquer momento com o comando `vsce space select`.
