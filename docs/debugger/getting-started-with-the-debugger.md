---
title: Saiba como depurar usando o depurador do Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1629e98c6d0afa4d259b7b983d1efe0633321c13
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468722"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Tutorial: Aprenda a depurar usando o Visual Studio

Este artigo apresenta os recursos do depurador do Visual Studio no passo a passo. Se você quiser uma exibição de alto nível dos recursos do depurador, consulte [tour pelos recursos do depurador](../debugger/debugger-feature-tour.md). Quando você *depurar seu aplicativo*, isso normalmente significa que você está executando seu aplicativo com o depurador anexado. Quando você fizer isso, o depurador fornece várias maneiras de ver o que está fazendo o seu código enquanto ele é executado. Você pode percorrer seu código e examinar os valores armazenados em variáveis, você pode definir inspeções em variáveis para ver quando os valores são alterados, você pode examinar o caminho de execução do seu código, ver se uma ramificação de código está em execução, e assim por diante. Se essa for a primeira vez que você tentou depurar o código, você talvez queira ler [depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md) antes de prosseguir com este artigo.

|         |         |
|---------|---------|
|  ![ícone de câmera para vídeo](../install/media/video-icon.png "Assistir a um vídeo")  |    [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sobre depuração, que mostra etapas semelhantes. |

Embora o aplicativo de demonstração é c# e C++, os recursos são aplicáveis ao Visual Basic, JavaScript e outras linguagens com suporte pelo Visual Studio (exceto onde observado). As capturas de tela estão em c#.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Inicie o depurador e atingir pontos de interrupção.
> * Saiba mais sobre os comandos para percorrer o código no depurador
> * Inspecionar variáveis em dicas de dados e janelas do depurador
> * Examinar a pilha de chamadas

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter o Visual Studio 2017 instalado e o **desenvolvimento de área de trabalho do .NET** ou **desenvolvimento para Desktop com C++** carga de trabalho.

    Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

    Se você precisar instalar a carga de trabalho, mas já tiver o Visual Studio, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto** (selecione **Arquivo** > **Novo** > **Projeto**). O Instalador do Visual Studio é iniciado. Escolha o. **Desenvolvimento de área de trabalho líquido** ou **desenvolvimento para Desktop com C++** carga de trabalho, em seguida, escolha **modificar**.

## <a name="create-a-project"></a>Criar um projeto

1. No Visual Studio, escolha **Arquivo > Novo Projeto**.

2. Sob **Visual c#** ou **Visual C++**, escolha **área de trabalho do Windows**e, em seguida, no painel central, escolha **aplicativo de Console** ( **Aplicativo de Console do Windows** em C++).

    Se você não vir as **aplicativo de Console** modelo de projeto, clique no **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Escolha o *desenvolvimento de área de trabalho do .NET** ou **desenvolvimento para Desktop com C++** carga de trabalho, em seguida, escolha **modificar**.

3. Digite um nome como **get-iniciou-depuração** e clique em **Okey**.

    O Visual Studio cria o projeto.

4. Na *Program.cs* (c#) ou *debugging.cpp iniciado get* (C++), substitua o código a seguir

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    ```c++
    int main()
    {
        return 0;
    }
    ```

    com este código:

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }
   
        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }

    }

    /* Output:
        Drawing a rectangle
        Performing base class drawing tasks
        Drawing a triangle
        Performing base class drawing tasks
        Drawing a circle
        Performing base class drawing tasks
    */
    ```

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Inicie o depurador!

1. Pressione **F5** (**Depurar > Iniciar depuração**) ou o **iniciar depuração** botão ![iniciar depuração](../debugger/media/dbg-tour-start-debugging.png "iniciar depuração ") na barra de ferramentas Depurar.

     **F5** inicia o aplicativo com o depurador anexado ao aplicativo processar, mas no momento, não fizemos nada especial para examinar o código. Portanto, o aplicativo é carregado apenas e você verá a saída do console.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     Neste tutorial, vamos dar uma olhada mais próxima este aplicativo usando o depurador e obter recursos de uma olhada no depurador.

2. Pare o depurador pressionando a parada vermelha ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "parar depuração") botão.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

1. No `foreach` loop do `Main` função (`for` loop for em C++ `main` função), defina um ponto de interrupção clicando na margem esquerda da primeira linha de código.

    ![Defina um ponto de interrupção](../debugger/media/get-started-set-breakpoint.png "SetABreakPoint")

    Um círculo vermelho aparece em que você definiu o ponto de interrupção.

    Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não. 

6. Pressione **F5** ou o **iniciar depuração** botão, o aplicativo é iniciado, e o depurador executa a linha de código em que você definiu o ponto de interrupção.

    ![Um ponto de interrupção](../debugger/media/get-started-hit-breakpoint.png "HitABreakPoint")

    A seta amarela representa a instrução na qual o depurador pausou a, que também suspende a execução de aplicativo no mesmo ponto (esta instrução ainda não foi executada).

     Se o aplicativo não está em execução ainda, **F5** inicia o depurador e é interrompida no primeiro ponto de interrupção. Caso contrário, **F5** continua executando o aplicativo para o próximo ponto de interrupção.

    Pontos de interrupção são um recurso útil quando você sabe que a linha de código ou a seção de código que você deseja examinar em detalhes.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar pelo código no depurador usando comandos de etapa

Em grande parte, podemos usar os atalhos de teclado aqui, porque ele é uma boa maneira de obter rápida no seu aplicativo em execução no depurador (comandos equivalentes, como o menu de comandos são mostrados entre parênteses).

1. Pressione **F11** (ou escolha **Depurar > intervir**) uma vez (várias vezes em c#) até que você pause sobre o `shape.Draw` chamada de método no `Main` método (`shape->Draw` em C++).

1. Pressione **F11** mais uma vez para avançar no código para o `Rectangle` classe.

     ![Use F11 para entrar em código](../debugger/media/get-started-f11.png "F11 intervir")

     F11 é o **intervir** de comando e avança a instrução de um de execução do aplicativo por vez. F11 é uma boa maneira para examinar o fluxo de execução em que a maioria dos detalhes. (Para mover mais rapidamente por meio de código, vamos mostrar algumas outras opções também.) Por padrão, o depurador ignora o código de não usuário (se você quiser obter mais detalhes, consulte [Just My Code](../debugger/just-my-code.md)).

2. Pressione **F10** (ou escolha **Depurar > Depuração parcial**) algumas vezes até que o depurador interrompe no `base.Draw` chamada de método (`Shape::Draw` em C++) e, em seguida, pressione **F10** mais uma vez.

     ![Use F10 para código Step Over](../debugger/media/get-started-step-over.png "F10 Step Over")

     Observe neste momento que o depurador não entra na `Draw` método da classe base (`Shape`). **F10** avança o depurador sem entrar em funções ou métodos no código do aplicativo (o código ainda é executado). Pressionando F10 na `base.Draw` (ou `Shape::Draw`) chamada de método (em vez de **F11**), podemos ignorei o código de implementação para `base.Draw` (que talvez podemos não estão interessados no momento).

## <a name="navigate-code-using-run-to-click"></a>Navegar pelo código usando executar com um clique

5. No editor de códigos, role para baixo e passe o mouse sobre o `Console.WriteLine` método (`std::cout` em C++) nos `Triangle` classe até que o verde **executar com um clique** botão ![executar com um clique] (../debugger/media/dbg-tour-run-to-click.png " RunToClick") aparece à esquerda.

     ![Usar o executar para clicar recurso](../debugger/media/get-started-run-to-click.png "executar com um clique")

    >  [!NOTE]
    > O **executar com um clique** há de novo no botão [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Se você não vir o botão de seta verde, use **F11** neste exemplo em vez disso, para avançar o depurador ao lugar certo.

6. Clique o **executar com um clique** botão ![executar com um clique](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Usar esse botão é semelhante à configuração de um ponto de interrupção temporário. **Executar com um clique** é útil para obter rapidamente em torno de dentro de uma região visível do código do aplicativo (você pode clicar em qualquer arquivo aberto).

    O depurador avança para o `Console.WriteLine` implementação do método para o `Triangle` classe (`std::cout` em C++).

    Enquanto estiver em pausa, você pode observar um erro de digitação! A saída de "Desenho um trangle" está incorreto. Podemos corrigi-la aqui ao executar o aplicativo no depurador.

## <a name="edit-code-and-continue-debugging"></a>Editar o código e continuar a depuração

1. Clique em "Desenho um trangle" e digite uma correção, alterando "trangle" para "triângulo".

1. Pressione **F11** uma vez e você ver que o depurador avança novamente.

    > [!NOTE]
    > Dependendo de qual tipo de código que você edita no depurador, você verá uma mensagem de aviso. Em alguns cenários, o código precisará recompilar antes de continuar.

## <a name="step-out"></a>Depuração circular

Digamos que você terminar de examinar o `Draw` método no `Triangle` classe e você quiser tirar proveito de função, mas mantenha-se no depurador. Você pode fazer isso usando o **depuração circular** comando.

1. Pressione **Shift** + **F11** (ou **Depurar > Depuração circular**).

     Este comando retoma a execução do aplicativo (e avança o depurador) até que retorna a função atual.

     Você deve ter voltado a `foreach` em um loop a `Main` método (`for` loop for em C++).

## <a name="restart-your-app-quickly"></a>Reinicie o aplicativo rapidamente

Clique o **reinicie** ![aplicativo reiniciar](../debugger/media/dbg-tour-restart.png "RestartApp") botão na barra de ferramentas Depurar (**Ctrl** + **Shift**   +  **F5**).

Quando você pressiona **reiniciar**, ele economiza tempo em comparação com o aplicativo de parar e reiniciar o depurador. O depurador pausa no primeiro ponto de interrupção é atingido pela execução de código.

O depurador novamente para no ponto de interrupção definido, além de `foreach` loop (`for` loop for em C++).

## <a name="inspect-variables-with-data-tips"></a>Inspecionar variáveis com dicas de dados

Recursos que permitem que você inspecione as variáveis são um dos recursos mais úteis do depurador, e há diferentes maneiras de fazê-lo. Muitas vezes, quando você tenta depurar um problema, você está tentando descobrir se as variáveis são armazenar os valores que você espera que eles têm em um momento específico.

1. Enquanto está em pausa na `foreach` loop (`for` loop for em C++), pressione **F11** depois.

1. Passe o mouse sobre o `shapes` objeto e você verá o valor de propriedade padrão, o `Count` propriedade.

1. Expanda o `shapes` objeto para ver todas as suas propriedades, como o primeiro índice da matriz `[0]`, que tem um valor de `Rectangle` (c#) ou um endereço de memória (C++).

     ![Exibir uma dica de dados](../debugger/media/get-started-data-tip.png "exibir uma dica de dados")

    Muitas vezes, durante a depuração, você deseja uma maneira rápida de verificar valores de propriedade em objetos e as dicas de dados são uma boa maneira de fazê-lo.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecionar variáveis com as janelas Autos e locais

1. Examine os **automóveis** janela na parte inferior do editor de código.

     ![Inspecionar variáveis na janela Autos](../debugger/media/get-started-autos-window.png "janela Autos")

    No **Autos** janela, você verá as variáveis e seu valor atual. O **automóveis** janela mostra todas as variáveis usadas na linha atual ou a linha anterior (em C++, a janela mostra as variáveis nas três linhas de código anteriores. Verifique a documentação para o comportamento específico do idioma).

    > [!NOTE]
    > No JavaScript, o **Locals** janela tem suporte, mas não a **Autos** janela.

2. Em seguida, examine os **Locals** janela, em uma guia ao lado de **Autos** janela.

    O **Locals** janela mostra as variáveis que estão na atual [escopo](https://www.wikipedia.org/wiki/Scope_(computer_science)).

## <a name="set-a-watch"></a>Definir uma inspeção

1. Na janela do editor de código principal, clique com botão direito do `shapes` do objeto e escolha **Adicionar inspeção**.

    O **inspeção** janela é aberta na parte inferior do editor de código. Você pode usar um **inspeção** janela para especificar uma variável (ou uma expressão) que você deseja que fique de olho no.

    Agora, você tem uma inspeção ativada a `shapes` objeto e você pode ver seu valor mudam conforme você move o depurador. Ao contrário de outras janelas variáveis, o **inspeção** janela sempre mostra as variáveis que você está observando (eles estão esmaecidos quando fora do escopo).

## <a name="examine-the-call-stack"></a>Examinar a pilha de chamadas

1. Enquanto está em pausa na `foreach` loop (`for` loop for em C++), clique no **pilha de chamadas** janela, por padrão, abrir no painel inferior direito.

1. Clique em **F11** algumas vezes até ver o depurador pausa no `Circle.Draw` método no editor de códigos. Examine os **pilha de chamadas** janela.

    ![Examinar a pilha de chamadas](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    O **pilha de chamadas** janela mostra a ordem em que métodos e funções estão sendo chamadas. A linha superior mostra a função atual (o `Circle.Draw` ou `Circle::Draw` método neste aplicativo). A segunda linha mostra que `Circle.Draw` foi chamado a partir de `Main` método (`main` em C++) e assim por diante.

    >  [!NOTE]
    > O **pilha de chamadas** janela é semelhante à perspectiva de depuração em alguns IDEs como o Eclipse.

    A pilha de chamadas é uma boa maneira para examinar e entender o fluxo de execução de um aplicativo.

    Você pode clicar duas vezes uma linha de código para examinar esse código-fonte e que também altera o escopo atual que está sendo inspecionado pelo depurador. Essa ação não avance para o depurador.

    Você também pode usar os menus de atalho do **pilha de chamadas** janela para fazer outras coisas. Por exemplo, você pode inserir os pontos de interrupção em funções especificadas, Avançar o depurador usando **executar até o Cursor**e examinar o código-fonte. Para obter mais informações, consulte [como: examinar a pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Alterar o fluxo de execução

1. Com o depurador em pausa na `Circle.Draw` chamada de método, pressione **F11** algumas vezes até que o depurador faz uma pausa sobre o `base.Draw` chamada de método (`Shape::Draw` em C++).

1. Use o mouse, selecione a seta amarela (o ponteiro de execução) à esquerda e mova a seta amarela para cima de uma linha para o `Console.WriteLine` (`std::cout` em C++) chamada de método.

1. Pressione **F11** mais uma vez.

    O depurador executa novamente os `Console.WriteLine` método (`std::cout` em C++).

    Alterando o fluxo de execução, você pode fazer coisas como caminhos de execução de código diferente de teste ou execute novamente o código sem reiniciar o depurador.

    > [!WARNING]
    > Geralmente, você precisa ter cuidado com esse recurso, e você verá um aviso na dica de ferramenta. Você pode ver outros avisos, muito. Movendo o ponteiro não é possível reverter o seu aplicativo para um estado anterior do aplicativo.

1. Pressione **F5** para continuar a execução do aplicativo.

    Parabéns por concluir este tutorial.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como iniciar o depurador, percorrer o código e inspecionar variáveis. Você talvez queira obter uma visão detalhada de recursos do depurador, juntamente com links para obter mais informações.

> [!div class="nextstepaction"]
> [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
