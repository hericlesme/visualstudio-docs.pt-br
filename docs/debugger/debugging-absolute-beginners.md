---
title: Depuração de código para iniciantes absolutos
description: Se você estiver depurando pela primeira vez, aprender alguns princípios para ajudá-lo a executar seu aplicativo no modo de depuração com o Visual Studio
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42a04a64f5ed7f62f4b01f703efa85e36aa854ff
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39131863"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Como depurar para iniciantes absolutos

Sem falhar, o código que escrevemos, como os desenvolvedores de software sempre não faz o que esperávamos-lo a fazer. Às vezes, ele faz algo completamente diferente! Quando isso acontece, a próxima tarefa é imaginar o porquê e embora nós pode ficar tentados a apenas manter olhando nosso código para horas, é muito mais fácil e eficiente usar uma ferramenta de depuração, ou do depurador.

Um depurador, infelizmente, não é algo que magicamente pode revelar todos os problemas ou "bugs" em nosso código. *Depuração* significa executar o código passo a passo em uma ferramenta de depuração, como o Visual Studio, para localizar o ponto exato em que você cometeu um erro de programação. Você, em seguida, entender quais correções que você precisa fazer em seu código e ferramentas de depuração geralmente permitem que você faça alterações temporárias para que possa continuar a execução do programa.

Usando um depurador com eficiência também é uma habilidade que leva tempo e prática para saber mais, mas, por fim, é uma tarefa fundamental para todo desenvolvedor de software. Neste artigo, em seguida, podemos introduzir os princípios fundamentais de depuração e fornecer dicas para você começar.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Esclarecer o problema, perguntando-se as perguntas certas

Ele ajuda a esclarecer o problema que você executou em antes de tentar corrigi-lo. Esperamos que você já teve um problema em seu código, caso contrário, você não esteja aqui tentando descobrir como depurá-lo! Portanto, antes de iniciar a depuração, verifique se que você identificou o problema que você está tentando resolver:

* O que você esperava seu código para fazer?

* Em vez disso, o que aconteceu?

    Se você executou um erro (exceção) durante a execução de seu aplicativo, que pode ser uma boa ideia! Uma exceção é um evento inesperado encontrado ao executar o código, geralmente um erro de algum tipo. Uma ferramenta de depuração pode levá-lo para o local exato em seu código onde ocorreu a exceção e pode ajudá-lo a investigar as possíveis correções.

    Se algo acontecer, o que é o sintoma do problema? Já pode onde esse problema ocorreu em seu código? Por exemplo, se seu código exibe um texto, mas o texto está incorreto, você sabe que seus dados são inválidos ou o código que define o texto de exibição tem algum tipo de bug. Percorrendo o código em um depurador, você pode examinar cada alteração para suas variáveis para descobrir exatamente quando e como os valores incorretos são atribuídos.

## <a name="examine-your-assumptions"></a>Examine suas suposições

Antes de investigar um bug ou um erro, considere as suposições que fez com que você espera que um determinado resultado. Suposições ocultas ou desconhecidas podem obter em termos de identificação de um problema, mesmo quando você estiver procurando diretamente a causa do problema em um depurador. Você pode ter uma longa lista de possíveis suposições! Aqui estão algumas perguntas se perguntar desafie suas suposições.

* Você está usando a API à direita (ou seja, o objeto à direita, função, método ou propriedade)? Uma API que você está usando pode não ser o que você acha que ele faz. (Depois de analisar a chamada à API no depurador, corrigi-lo pode exigir uma viagem para a documentação para ajudar a identificar a API correta.)

* Você está usando uma API corretamente? Talvez você usado o direito de API, mas não usá-lo da maneira correta.

* Seu código contém nenhum erro de digitação? Alguns erros de digitação, como um erro de ortografia simple de um nome de variável, podem ser difíceis de ver, especialmente ao trabalhar com idiomas que não exigem que as variáveis sejam declaradas antes de serem usados.

* Você fazer uma alteração em seu código e supor que ele não está relacionado ao problema que você está vendo?

* Você esperava que um objeto ou variável para conter um determinado valor (ou um determinado tipo de valor) que é diferente do que realmente aconteceu?

* Você sabe a intenção do código? Geralmente é mais difícil de depurar a outra pessoa do código. Se não for seu código, é possível que talvez você precise gastar tempo aprendendo exatamente o que o código faz antes de depurá-lo efetivamente.

    > [!TIP]
    > Ao escrever código, comece pequeno e começar com o código que funciona! (BOM código de exemplo é útil aqui.) Às vezes, é mais fácil de corrigir um conjunto grande ou complicado de código começando com um pequeno trecho de código que demonstra a tarefa principal que você está tentando alcançar. Em seguida, você pode modificar ou adicionar código de forma incremental, testes em cada ponto de erros.

Por questione suas suposições, você pode reduzir o tempo necessário para localizar um problema em seu código. Você também pode reduzir o tempo necessário para corrigir um problema.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Depurar seu código no modo para localizar onde ocorreu o problema de depuração

Quando você normalmente executa um aplicativo, você verá erros e resultados incorretos somente depois que o código foi executada. Um programa também pode encerrar inesperadamente sem informando o porquê.

Executar um aplicativo em um depurador, também chamado de *modo de depuração*, significa que o depurador monitora ativamente tudo o que está acontecendo como as execuções de programa. Ele também permite que você pause o aplicativo a qualquer momento para examinar seu estado e, em seguida, percorrer o código linha por linha para observar todos os detalhes, como acontece.

No Visual Studio, você entrar no modo de depuração usando **F5** (ou o **Debug** > **iniciar depuração** comando de menu ou a **iniciar depuração**  botão ![iniciar depuração](../debugger/media/dbg-tour-start-debugging.png "iniciar depuração")) na barra de ferramentas Depurar. Se todas as exceções ocorrem, o auxiliar de exceção do Visual Studio leva você até o ponto exato em que a exceção ocorreu e fornece outras informações úteis.

Se você não receber uma exceção, você provavelmente terá uma boa ideia onde procurar o problema em seu código. Isso em que você usa *pontos de interrupção* com o depurador para dar a oportunidade de examinar seu código mais cuidadosamente. Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica onde o Visual Studio deve pausar o código em execução para que você pode dar uma olhada em como os valores das variáveis, ou o comportamento de memória ou a sequência na qual o código é executado.

No Visual Studio, você pode configurar rapidamente um ponto de interrupção clicando na margem esquerda ao lado de uma linha de código. Ou coloque o cursor em uma linha e pressione **F9**.

Para ajudar a ilustrar esses conceitos, nós o levamos por meio de um código de exemplo que já tem vários bugs. Estamos usando c#, mas os recursos de depuração se aplicam ao Visual Basic, C++, JavaScript, Python e outras linguagens com suporte.

### <a name="create-a-sample-app-with-some-bugs"></a>Criar um aplicativo de exemplo (com alguns bugs)

Em seguida, criaremos um aplicativo que contém alguns bugs.

1. Você deve ter instalado o Visual Studio e qualquer uma de. **Desenvolvimento de área de trabalho líquido** carga de trabalho ou o. **NET Core desenvolvimento multiplataforma** a carga de trabalho instalada, dependendo do tipo de qual aplicativo você deseja criar.

    Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

    Se você precisa instalar a carga de trabalho, mas já tiver o Visual Studio, clique em **ferramentas** > **obter ferramentas e recursos**. O Instalador do Visual Studio é iniciado. Escolha o. **Desenvolvimento de área de trabalho líquido** (ou. **NET Core desenvolvimento multiplataforma**) carga de trabalho, em seguida, escolha **modificar**.

1. Abra o Visual Studio e, em seguida, escolha **arquivo** > **New** > **projeto**.

1. Escolha um modelo para o código do aplicativo.

    Para o .NET Framework, no **novo projeto** diálogo caixa, escolha **Visual c#**, **área de trabalho do Windows** da seção de modelos instalados e, em seguida, no painel central, selecione  **Aplicativo do console (.NET Framework)**.

    Para o .NET Core na **novo projeto** caixa de diálogo, escolha **Visual c#**, **.NET Core** na seção modelos instalados e, em seguida, no painel central, selecione  **Aplicativo (.NET Core) do console**.

    Se você não vir essas modelo, você deve instalar a carga de trabalho apropriada (consulte as etapas anteriores).

1. No **nome** , digite **ConsoleApp FirstApp** e clique em **Okey**.

    Visual Studio cria o projeto de console, que é exibido no Gerenciador de soluções, no painel direito.

1. Na *Program.cs*, substitua todo o código padrão pelo código a seguir:

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Nossa intenção para que esse código é exibir o nome do galaxy, a distância até a galáxia e o tipo de galaxy em uma lista. Para depurar, é importante entender a intenção do código. Aqui está o formato para uma linha na lista que desejamos mostrar na saída:

    *nome Galaxy*, *distância*, *tipo galaxy*.

### <a name="run-the-app"></a>Executar o aplicativo

1. Pressione **F5** ou o **iniciar depuração** botão ![iniciar depuração](../debugger/media/dbg-tour-start-debugging.png "iniciar depuração") na barra de ferramentas de depuração, localizado acima do editor de código.

    O aplicativo é iniciado e haverá qualquer exceção mostrada em contato pelo depurador. No entanto, a saída que você pode ver na janela do console é não o que você espera. Aqui está a saída esperada:

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Porém, podemos ver isso em vez disso:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Analisar a saída e em nosso código, sabemos que `GType` é o nome da classe que armazena o tipo galaxy. Estamos tentando mostrar o tipo real galaxy (por exemplo, "espiral"), não o nome da classe!

### <a name="debug-the-app"></a>Depurar o aplicativo

1. Com o aplicativo ainda em execução, defina um ponto de interrupção clicando na margem esquerda ao lado de `Console.WriteLine` chamada de método nesta linha de código.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Quando você define o ponto de interrupção, um ponto vermelho aparece na margem esquerda.

    Como podemos ver um problema na saída, vamos começar depuração examinando o código anterior que define a saída no depurador.

1. Clique o **reinicie** ![aplicativo reiniciar](../debugger/media/dbg-tour-restart.png "RestartApp") botão na barra de ferramentas Depurar (**Ctrl** + **Shift**   +  **F5**).

    O aplicativo faz uma pausa no ponto de interrupção que você definir. O hightlighting amarelo indica onde o depurador estiver pausado (a linha amarela de código ainda não foi executada).

1. Passe o mouse sobre o `GalaxyType` variável à direita e, em seguida, à esquerda do ícone de chave inglesa, expanda `theGalaxy.GalaxyType`. Você verá que `GalaxyType` contém uma propriedade `MyGType`, e o valor da propriedade é definido como `Spiral`.

    ![Inspecionar uma variável](../debugger/media/beginners-inspect-variable.png)

    "Espiral" é, na verdade, o valor correto que você estava aguardando para imprimir no console! Portanto, é um bom começo para que você pode acessar esse valor nesse código enquanto executa o aplicativo. Nesse cenário, estamos usando a API incorreta. Veremos se podemos corrigir isso durante a execução de código no depurador.

1. O mesmo código, durante a depuração ainda, coloque o cursor no final da `theGalaxy.GalaxyType` e altere-a para `theGalaxy.GalaxyType.MyGType`. Embora você possa fazer essa alteração, o editor de código mostra um erro indicando que ele não é possível compilar esse código.

    ![Erro de sintaxe](../debugger/media/beginners-edit.png)

1. Clique em **edite** na **editar e continuar** caixa de mensagem. Você verá uma mensagem de erro no agora o **Error List** janela. O erro indica que o `'object'` não contém uma definição para `MyGType`.

    ![Erro de sintaxe](../debugger/media/beginners-no-definition.png)

    Mesmo que definimos cada galaxy com um objeto do tipo `GType` (que tem o `MGType` propriedade), o depurador não reconhece o `theGalaxy` objeto como um objeto do tipo `GType`. O que está acontecendo? Você deseja procurar por meio de qualquer código que define o tipo de galaxy. Quando você fizer isso, você verá que o `GType` classe definitivamente tem uma propriedade de `MyGType`, mas algo não está correto. A mensagem de erro sobre `object` acaba sendo pista; para o interpretador de linguagem, o tipo parece ser um objeto do tipo `object` em vez de um objeto do tipo `GType`.

1. Procurando por meio de seu código relacionado à definição do tipo galaxy, localize o `GalaxyType` propriedade do `Galaxy` classe é especificado como `object` em vez de `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Altere o código anterior para:

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Clique o **reinicie** ![aplicativo reiniciar](../debugger/media/dbg-tour-restart.png "RestartApp") botão na barra de ferramentas Depurar (**Ctrl** + **Shift**   +  **F5**) para recompilar o código e reiniciar.

    Agora, quando o depurador pausa no `Console.WriteLine`, é possível focalizar `theGalaxy.GalaxyType.MyGType`e verá que o valor é definido adequadamente.

1. Remover o ponto de interrupção clicando no círculo de ponto de interrupção na margem esquerda (ou o botão direito do mouse e escolha **ponto de interrupção** > **Excluir ponto de interrupção**) e, em seguida, pressione **F5** para continuar.

    O aplicativo é executado e exibe a saída. Ele se parece muito bom agora, mas você observará uma coisa; você esperava o galaxy pequena nuvem de Magellanic apareça como uma galáxia Irregular na saída do console, mas ele não mostra nenhum tipo galaxy em todos os.

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Defina um ponto de interrupção nessa linha de código.

    ```csharp
    public GType(char type)
    ```

    Esse código é onde o tipo de galaxy for definido, portanto, queremos examinar um perto-lo.

1. Clique o **reinicie** ![aplicativo reiniciar](../debugger/media/dbg-tour-restart.png "RestartApp") botão na barra de ferramentas Depurar (**Ctrl** + **Shift**   +  **F5**) para reiniciar.

    O depurador faz uma pausa na linha de código em que você definir o ponto de interrupção.  

1. Passe o mouse sobre o `type` variável. Você verá um valor de `S` (seguindo o código de caractere). Você está interessado em um valor de `I`, uma vez que você sabe que é um tipo galaxy Irregular.

1. Pressione **F5** e passe o mouse sobre o `type` variável novamente. Repita essa etapa até que você vê um valor de `I` no `type` variável.

    ![Inspecionar uma variável](../debugger/media/beginners-inspecting-data.png)

1. Agora, pressione **F11** (**Debug** > **intervir** ou o **intervir** botão na barra de ferramentas de depuração).

    **F11** avança o depurador (e executa o código) em uma instrução por vez. **F10** (**Step Over**) é um comando semelhante, e ambos são extremamente úteis ao aprender a usar o depurador.

1. Pressione **F11** até que você interrompa na linha de código no `switch` instrução para um valor de 'I'. Aqui, você pode ver um claro problema resultante de um erro de digitação. Você esperava que o código para ir para onde ela define o `MyGType` como um irregulares tipo galaxy, mas o depurador em vez disso, ignora esse código completamente e faz uma pausa sobre o `default` seção o `switch` instrução.

    ![Encontrar um erro de digitação](../debugger/media/beginners-typo.png)

    Examinar o código, você verá um erro de digitação no `case 'l'` instrução. Ele deve ser `case 'I'`.

1. Clique no código de `case 'l'`e substituí-lo por ' 'I' case.

1. Remova o ponto de interrupção e, em seguida, clique no **reiniciar** botão reiniciar o aplicativo.

    Os erros são corrigidos agora e você verá a saída que você espera!

    Pressione qualquer tecla para concluir o aplicativo.

## <a name="summary"></a>Resumo

Quando você vir um problema, use o depurador e [comandos de etapa](../debugger/navigating-through-code-with-the-debugger.md) tais como **F10** e **F11** para localizar a região de código com o problema.

> [!NOTE]
> Se for difícil de identificar a região de código onde o problema ocorre, defina um ponto de interrupção no código que é executado antes que ocorra o problema e, em seguida, usar comandos de etapa até que você veja o problema manifesto. Você também pode usar [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) para fazer as mensagens para o **saída** janela. Por examinar mensagens registradas (e observar que as mensagens que ainda não foram conectadas!), geralmente você pode isolar a região de código com o problema. Talvez você precise repetir esse processo várias vezes para restringir esse conjunto.

Quando você encontrar a região de código com o problema, use o depurador para investigar. Para encontrar a causa de um problema, inspecione o código do problema durante a execução de seu aplicativo no depurador:

* [Inspecionar variáveis](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) e verifique se eles contêm os tipos de valores que eles devem conter. Se você encontrar um valor incorreto, descobrir onde o valor incorreto foi definido (para localizar onde o valor foi definido, talvez você precise a reiniciar o depurador, examine os [pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md), ou ambos).

* Verifique se o seu aplicativo está executando o código que você espera. (Por exemplo, no aplicativo de exemplo, se espera que o código para a instrução switch definir o tipo de galaxy como irregulares, mas o aplicativo ignorou o código devido a erro de digitação de.)

> [!TIP]
> Você pode usar um depurador para ajudá-lo a encontrar bugs. Uma ferramenta de depuração poderá localizar bugs *para você* somente se souber a intenção do seu código. Uma ferramenta somente pode saber a intenção do seu código se você, o desenvolvedor expressar essa intenção. Gravando [testes de unidade](../test/improve-code-quality.md) é como fazer isso.

## <a name="next-steps"></a>Próximas etapas

Neste artigo, você aprendeu alguns conceitos gerais de depuração. Em seguida, você pode começar a aprender a depurar com o Visual Studio.

> [!div class="nextstepaction"]
> [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
