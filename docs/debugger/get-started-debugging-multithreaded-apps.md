---
title: Saiba como depurar aplicativos multithread
description: Depurar usando as janelas de pilhas paralelas e inspeção paralela no Visual Studio
ms.custom: H1HackMay2017
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11cb05ea81f086cf8c26e3058850968a909b84e3
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468677"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Começar a depurar aplicativos multi-threaded no Visual Studio
Visual Studio fornece várias ferramentas e os elementos de interface do usuário para ajudá-lo a depurar aplicativos multi-threaded. Este tutorial mostra como usar marcadores de thread, o **pilhas paralelas** janela, o **inspeção paralela** janela pontos de interrupção condicionais e pontos de interrupção de filtro. Este tutorial leva apenas alguns minutos, mas concluí-la você se familiarizará com os recursos para depurar aplicativos multithread.

|         |         |
|---------|---------|
|  ![ícone de câmera para vídeo](../install/media/video-icon.png "Assistir a um vídeo")  |    [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) sobre depuração com multithread que mostra etapas semelhantes. |

Outros tópicos fornecem informações adicionais sobre como usar outras ferramentas de depuração multithread:

- Para um tópico semelhante que mostra como usar o **local de depuração** barra de ferramentas e o **Threads** janela, consulte [passo a passo: depurar um aplicativo multi-threaded](../debugger/how-to-use-the-threads-window.md).

- Para um tópico semelhante com um exemplo que usa <xref:System.Threading.Tasks.Task> (código gerenciado) e o tempo de execução de simultaneidade (C++), consulte [passo a passo: depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md). Para obter dicas de depuração gerais que se aplicam a tipos de aplicativos multithread mais, leia este tópico e tópico vinculado.
  
Para iniciar este tutorial, você precisará de um projeto de aplicativo multithread. Siga as etapas listadas aqui para criar o projeto.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Para criar o projeto de aplicativo multithread  
  
1.  Sobre o **arquivo** menu, escolha **New** e, em seguida, clique em **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Clique no idioma de sua escolha: **Visual c#**, **Visual C++**, ou **Visual Basic**.  
  
3.  Sob **área de trabalho do Windows**, escolha **aplicativo de Console**.  
  
4.  No **nome** caixa, digite o nome MyThreadWalkthroughApp.  
  
5.  Clique em **OK**.  
  
     Um novo projeto de console é exibido. Quando o projeto tiver sido criado, um arquivo de origem aparecerá. Dependendo da linguagem escolhida, o arquivo de origem pode ser chamado Module1.vb, mythreadwalkthroughapp. cpp ou Program.cs.  
  
6.  Exclua o código que aparece no arquivo de origem e substitua-o com o código de exemplo mostrado aqui.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  Sobre o **arquivo** menu, clique em **Salvar tudo**.  
  
#### <a name="to-begin-the-tutorial"></a>Para começar o tutorial  
  
-   No editor de código fonte, procure o código a seguir: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Para iniciar a depuração  
  
1.  Clique na medianiz esquerda dos `Thread.Sleep` ou `this_thread::sleep_for` instrução para inserir um novo ponto de interrupção.  
  
     Na medianiz no lado esquerdo do editor de código fonte, um círculo vermelho aparece. Isso indica que um ponto de interrupção agora está definido nesse local. 
  
2.  Sobre o **Debug** menu, clique em **iniciar depuração** (**F5**).  
  
     Visual Studio compila a solução, o aplicativo começa a ser executado com o depurador anexado e, em seguida, o aplicativo for interrompida no ponto de interrupção.  
  
    > [!NOTE]
    > Se você alternar o foco para a janela do console, clique na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela para retornar o foco para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  No editor de código fonte, localize a linha que contém o ponto de interrupção:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3)); 
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Para descobrir o marcador de thread  

1.  Na barra de ferramentas Depurar, clique o **Mostrar Threads em origem** botão ![Mostrar Threads em origem](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Pressione **F11** uma vez para Avançar a linha de um do depurador de código.
  
3.  Examine a medianiz no lado esquerdo da janela. Nessa linha, você verá uma *marcador de thread* ícone ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") que se parece com dois threads de pano. O marcador de thread indica que um thread está parado nesse local.

    Observe que um marcador de thread pode ser escondido parcialmente por um ponto de interrupção. 
  
4.  Passe o ponteiro sobre o marcador de thread. Um DataTip aparece. O DataTip mostra o nome e o número de ID do thread para cada thread parado. Nesse caso, o nome é provavelmente `<noname>`. 
  
5.  Clique com botão direito no marcador de thread para ver as opções disponíveis no menu de atalho.
    
## <a name="ParallelStacks"></a>Exiba o local de Threads

No **pilhas paralelas** janela, você pode alternar entre um modo de exibição de Threads e (para a programação baseada em tarefa) o modo de exibição de tarefas e você pode exibir informações de pilha de chamada para cada thread. Neste aplicativo, podemos usar o modo de exibição de Threads.

1. Abra o **pilhas paralelas** janela escolhendo **Depurar > Windows > pilhas paralelas**. Você deverá ver algo semelhante a esta (as informações exatas será diferentes dependendo do local atual de cada thread, o hardware e a linguagem de programação).

    ![Janela de pilhas paralelas](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    Neste exemplo, da esquerda para direita podemos obter essas informações para código gerenciado:
    
    - O thread principal (lado esquerdo) foi interrompido no `Thread.Start` (o ponto de interrupção é indicado pelo ícone de marcador de thread ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Dois threads inseriu a `ServerClass.InstanceMethod`, um dos quais é o thread atual (seta amarela), enquanto o outro thread foi interrompido no `Thread.Sleep`.
    - Um novo thread (à direita) também está iniciando (interrompido no `ThreadHelper.ThreadStart`).

2.  Clique com botão direito entradas na **pilhas paralelas** janela para ver as opções disponíveis no menu de atalho.

    Você pode executar várias ações desses menus de atalho, mas para este tutorial, mostraremos mais desses detalhes na **inspeção paralela** janela (próximas seções).

    > [!NOTE]
    > Se você estiver mais interessado em ver uma lista de exibir informações sobre cada thread, use o **Threads** janela em vez disso. Ver [instruções passo a passo: depurar um aplicativo multi-threaded](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Definir uma inspeção em uma variável

1. Abra o **inspeção paralela** janela escolhendo **Depurar > Windows > inspeção paralela > paralela inspeção 1**.

2. Clique na célula em que você consulte os `<Add Watch>` texto (ou a célula de cabeçalho vazio na coluna 4 de maio), tipo `data`, e pressione Enter.

    Os valores para a variável de dados para cada thread aparecem na janela.

3. Clique novamente na célula em que você consulte os `<Add Watch>` texto (ou a célula de cabeçalho vazio na coluna 5ª), tipo `count`, e pressione Enter.

    Os valores para a variável de contagem para cada thread aparecem na janela. (Se você não vir ainda muitas informações, tente pressionando F11 mais algumas vezes para Avançar a execução dos threads no depurador).

    ![Janela de inspeção em paralelo](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Clique em uma das linhas na janela para ver as opções disponíveis.

## <a name="flagging-and-unflagging-threads"></a>Sinalizando e removendo a sinalização de threads  
Você pode sinalizar os threads que você deseja dar atenção especial. Sinalizar threads é uma boa maneira de manter o controle de threads importantes e ignorar threads que você não se importa.  
  
#### <a name="to-flag-threads"></a>Para sinalizar threads  

1. No **inspeção paralela** janela, mantenha pressionada a tecla SHIFT e selecionar várias linhas.

2. Clique com botão direito e escolha **sinalizador**.

    Agora, todos os threads são sinalizados. Agora, você pode filtrar para mostrar somente threads sinalizados.
  
3.  No **inspeção paralela** janela, localizar o **Mostrar somente Threads sinalizados** botão ![Mostrar Threads sinalizados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Clique o **Mostrar somente Threads sinalizados** botão.  
  
    Somente o thread sinalizado agora aparece na lista.

    > [!TIP]
    > Quando você sinalizou alguns threads, pode ser uma linha de código no editor de códigos com o botão direito e escolha **executar Threads sinalizados Cursor** (certifique-se de que você escolha entrará em todos os threads sinalizados de código). Isso irá pausar threads na linha selecionada de código, tornando mais fácil controlar a ordem de execução pelo [congelando e Descongelando threads](#bkmk_freeze).

5.  Clique o **Mostrar somente Threads sinalizados** botão para voltar ao **Mostrar todos os Threads** modo.
    
#### <a name="to-unflag-threads"></a>Para remover a sinalização de threads

Para remover a sinalização de threads, você pode clique com botão direito um ou mais threads sinalizados na **inspeção paralela** janela e escolha **Remover sinalização**.

## <a name="bkmk_freeze"></a> Congelando e Descongelando a execução do thread 

> [!TIP]
> Você pode congelar e descongelar (suspender e retomar) threads para controlar a ordem na qual threads executam o trabalho. Isso pode ajudá-lo a resolver problemas de simultaneidade, como deadlocks e condições de corrida.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para congelar e descongelar threads  
  
1.  No **inspeção paralela** janela, com todas as linhas selecionadas, clique com botão direito e selecione **congelar**.

    Na segunda coluna, um ícone de pausa agora é exibido para cada linha. O ícone de pausa indica que o thread está congelado.

2.  Desmarque as linhas, clicando em apenas uma linha.

3.  Uma linha com o botão direito e selecione **descongelar**.

    O ícone de pausa desaparece nesta linha, que indica que o thread não está congelado.

4.  Alterne para o editor de códigos e clique em **F11**. Somente as execuções de thread não congeladas.

    O aplicativo também pode criar uma instância de alguns novos threads. Observe que quaisquer novos threads são sem sinalização e não estão congelados.

## <a name="bkmk_follow_a_thread"></a> Execute um único Thread usando pontos de interrupção condicionais

Às vezes, pode ser útil acompanhar a execução de um único thread no depurador. Uma maneira de fazer isso é por congelar threads que não está interessado, mas em alguns cenários talvez você queira seguir um único thread sem congelamento de outros threads (para reprodução de um determinado de bug, por exemplo). Para seguir um thread sem congelamento de outros threads, você deve evitar a interrupção no código, exceto no thread em que você está interessado. Você pode fazer isso definindo uma [ponto de interrupção condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Você pode definir pontos de interrupção em diferentes condições, como o nome do thread ou a ID do thread. Outro método que pode ser útil é definir a condição nos dados que você sabe que serão exclusivos para cada thread. Isso é um cenário comum de depuração, no qual você está mais interessado em alguns valores de dados específico que em qualquer thread específico.

#### <a name="to-follow-a-single-thread"></a>A seguir um único thread

1. O ponto de interrupção que você criou anteriormente com o botão direito e escolha **condições**.

2. No **configurações de ponto de interrupção** , digite `data == 5` para a expressão condicional.

    ![Ponto de interrupção condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Se você estiver mais interessado em um thread específico, use um nome de thread ou a ID do thread para a condição. Para fazer isso na **configurações de ponto de interrupção** janela, selecione **filtro** em vez de **expressão condicional**e siga as dicas de filtro. Você talvez queira nomear seus threads no código do aplicativo (já que as IDs de threads alterar quando você reiniciar o depurador).

3. Fechar o **configurações de ponto de interrupção** janela.

4. Clique a reinicialização ![aplicativo reinicie](../debugger/media/dbg-tour-restart.png "RestartApp") botão reiniciar a sessão de depuração.

    Você será decifre o código no thread para o qual a variável de dados é 5. Examinar a seta amarela (contexto do depurador atual) a **inspeção paralela** janela para verificar se.

5. Agora, step over no código (F10) e intervir no código (F11) e siga a execução de thread único.

    Desde que a condição de ponto de interrupção é exclusiva para o thread e o depurador não usar quaisquer outros pontos de interrupção em outros threads (talvez seja necessário desabilitá-las), você pode step over no código e intervir no código sem alternar para outros threads.

    > [!NOTE]
    > Quando você avança o depurador, todos os threads serão executados. No entanto, o depurador não quebre em código em outros threads, a menos que um dos outros threads atinge um ponto de interrupção. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Mais informações sobre janelas de depuração multithread 

#### <a name="to-switch-to-another-thread"></a>Para alternar para outro thread 

- Para alternar para outro thread, consulte [como: alternar para outro Thread enquanto a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Para saber mais sobre as janelas de pilha paralela e inspeção paralela  
  
- Consulte [como: usar a janela de pilha paralela](../debugger/using-the-parallel-stacks-window.md) 

- Consulte [como: usar a janela Inspeção paralela](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como mudar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)
