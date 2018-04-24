---
title: Depurar com C++ usando o depurador do Visual Studio | Microsoft Docs
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: f591c4272dc50643dcb3c82f60d96fd218723405
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="debug-with-c-using-the-visual-studio-debugger"></a>Depurar com C++ usando o depurador do Visual Studio

O depurador do Visual Studio fornece muitos recursos poderosos para ajudá-lo a depurar seus aplicativos. Este tópico fornece uma maneira rápida de conhecer alguns dos recursos básicos.

## <a name="create-a-new-project"></a>Criar um novo projeto 

1. No Visual Studio, escolha **Arquivo > Novo Projeto**.

2. Em **Visual C++**, escolha **Área de Trabalho do Windows** e escolha **Aplicativo de Console do Windows** no painel central.

    Se você não vir o **aplicativo de Console do Windows** modelo de projeto, clique no **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Escolha o **desenvolvimento de área de trabalho com C++** carga de trabalho, escolha **modificar**.

3. Digite um nome como **MyDbgApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

4. Em MyDbgApp.cpp, substitua o código a seguir

    ```c++
    int main()
    {
        return 0;
    }
    ```

    por esse código (não remova `#include "stdafx.h"`):

    ```c++
    #include <list>  
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Definir um ponto de interrupção

Um *ponto de interrupção* é um marcador que indica onde o Visual Studio deve suspender a execução de código para que você pode dar uma olhada os valores das variáveis ou o comportamento de memória ou se deve ou não uma ramificação de código é obtendo executada. É o recurso mais básico na depuração.

1. Para definir o ponto de interrupção, clique na medianiz à esquerda do `doWork` chamada de função (ou selecione a linha de código e pressione **F9**).

    ![Definir um ponto de interrupção](../debugger/media/dbg-qs-set-breakpoint.png "definir um ponto de interrupção")

2. Agora, pressione **F5** (ou escolha **Depurar > Iniciar depuração**).

    ![Um ponto de interrupção](../debugger/media/dbg-qs-hit-breakpoint.png "um ponto de interrupção")

    A pausa do depurador onde você pode definir o ponto de interrupção. A instrução em que a execução do aplicativo e o depurador é pausada é indicada pela seta amarela. A linha com o `doWork` chamada de função ainda não foi executada.

    > [!TIP]
    > Se você tiver um ponto de interrupção em um loop ou recursão, ou se você tiver muitos pontos de interrupção que você frequentemente percorrer, use um [ponto de interrupção condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para certificar-se de que seu código está suspenso somente quando condições específicas forem atendidas. Um ponto de interrupção condicional economiza tempo e pode também facilitam a depurar problemas difíceis de reproduzir.

    Ao tentar depurar falhas relacionadas à memória em C++, você também pode usar pontos de interrupção para inspecionar os valores de endereço (procure por NULL) e contagens de referência. 

## <a name="navigate-code"></a>Navegue pelos códigos

Há diferentes comandos para instruir o depurador para continuar. Vamos mostrar um comando de navegação de código útil que há de novo no Visual Studio de 2017.

Enquanto está em pausa no ponto de interrupção, passe o mouse sobre a instrução `c1.push_back(20)` até que o verde **execução clique** botão ![executar em, clique em](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece e, em seguida, pressione a **Execução clique** botão.

![Execução clique](../debugger/media/dbg-qs-run-to-click.png "execução clique")

O aplicativo continua a execução, chamada `doWork`e faz uma pausa na linha de código em que você clicou no botão.

Comandos comuns do teclado usados para percorrer o código incluem **F10** e **F11**. Para obter mais instruções detalhadas, consulte o [guia do Iniciante](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecionar variáveis em um datatip

1. Na linha atual do código (indicado pelo ponteiro de execução amarelo), passe o mouse sobre o `c1` objeto com o mouse para mostrar um datatip.

    ![Exibir um datatip](../debugger/media/dbg-qs-data-tip.png "exibir um datatip")

    O datatip mostra o valor atual de `c1` variável e permite que você inspecione suas propriedades. Durante a depuração, se você vir um valor que você não espera, você provavelmente terá um bug nas linhas anteriores ou chamadas do código. 

2. Expanda datatip para examinar os valores de propriedade atual o `c1` objeto.

3. Se você deseja fixar o datatip para que você pode continuar a ver o valor de `c1` enquanto você executar o código, clique no ícone de pino pequeno. (Você pode mover o datatip fixado em um local conveniente.)

## <a name="edit-code-and-continue-debugging"></a>Edite o código e continuar a depuração

Se você identificar uma alteração que você deseja testar no seu código no meio de uma sessão de depuração, você pode fazer isso, muito.

1. Clique na segunda instância de `c2.front()` e alterar `c2.front()` para `c2.back()`.

2. Pressione **F10** (ou **Depurar > passar por**) algumas vezes para avançar o depurador e execute o código editado.

    ![Editar e continuar](../debugger/media/dbg-qs-edit-and-continue.gif "editar e continuar")

    **F10** avança a instrução de depurador um em uma hora, mas as etapas sobre funções em vez de avançá-los (ainda executa o código que você ignorar).

Para obter mais informações sobre como usar Editar e continuar e limitações de recursos, consulte [editar e continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como iniciar o depurador, percorrer o código e inspecionar variáveis. Você talvez queira obter uma visão de alto nível de recursos do depurador junto com links para mais informações.

> [!div class="nextstepaction"]
> [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
