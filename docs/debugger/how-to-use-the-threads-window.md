---
title: Depurar um aplicativo multithread
description: Depurar usando a janela Threads e a barra de ferramentas do local de depuração no Visual Studio
ms.custom: ''
ms.date: 05/18/2017
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
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65626bc483d7794c2adae141903783238a97eddd
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468459"
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>Passo a passo: Depurar um aplicativo multi-threaded no Visual Studio usando a janela Threads
O Visual Studio fornece um **Threads** elementos para ajudá-lo a depurar aplicativos multithread de interface de janela e outro usuário. Este tutorial mostra como usar o **Threads** janela e o **local de depuração** barra de ferramentas. Para obter informações sobre as outras ferramentas, consulte [começar a depurar aplicativos multissegmentados](../debugger/get-started-debugging-multithreaded-apps.md). Este tutorial leva apenas alguns minutos, mas concluí-la você se familiarizará com os recursos para depurar aplicativos multithread.   
  
Para iniciar este tutorial, você precisará de um projeto de aplicativo multithread. Siga as etapas listadas aqui para criar o projeto.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Para criar o projeto de aplicativo multithread  
  
1.  Sobre o **arquivo** menu, escolha **New** e, em seguida, clique em **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  No **tipo de projeto**s caixa, clique na linguagem de sua escolha: **Visual Basic**, **Visual c#**, ou **Visual C++**.  
  
3.  Sob **área de trabalho do Windows**, escolha **aplicativo de Console**.  
  
4.  No **nome** caixa, digite o nome MyThreadWalkthroughApp.  
  
5.  Clique em **OK**.  
  
     Um novo projeto de console é exibido. Quando o projeto tiver sido criado, um arquivo de origem aparecerá. Dependendo da linguagem escolhida, o arquivo de origem poderá ser chamado Module1.vb, Program.cs ou MyThreadWalkthroughApp.cpp  
  
6.  Exclua o código que aparece no arquivo de origem e substitua-o com o código de exemplo que aparece na seção "Criando um Thread" do tópico [criando Threads e passando dados na hora de início](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time).  
  
7.  Sobre o **arquivo** menu, clique em **Salvar tudo**.  
  
#### <a name="to-begin-the-tutorial"></a>Para começar o tutorial  
  
-   No editor de código fonte, procure o código a seguir:  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine()
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>Para iniciar a depuração  
  
1.  Clique na medianiz esquerda do `Console.WriteLine` instrução para inserir um novo ponto de interrupção.  
  
     Na medianiz no lado esquerdo do editor de código fonte, um círculo vermelho aparece. Isso indica que um ponto de interrupção agora está definido nesse local.  
  
2.  Sobre o **Debug** menu, clique em **iniciar depuração** (**F5**).  
  
     A depuração é iniciada, seu aplicativo de console começa a ser executado e, em seguida, para no ponto de interrupção.  
  
3.  Se a janela do aplicativo de console tiver o foco neste momento, clique na janela do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para retornar o foco para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  No editor de código fonte, localize a linha que contém o código a seguir:  
  
    ```VB  
    Thread.Sleep(5000)   
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```
  
#### <a name="to-discover-the-thread-marker"></a>Para descobrir o marcador de thread  

1.  Na barra de ferramentas Depurar, clique o **Mostrar Threads em origem** botão ![Mostrar Threads em origem](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker"). 
  
2.  Examine a medianiz no lado esquerdo da janela. Nessa linha, você verá uma *marcador de thread* ícone ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") que se parece com dois threads de pano. O marcador de thread indica que um thread está parado nesse local.  
  
3.  Passe o ponteiro sobre o marcador de thread. Um DataTip aparece. O DataTip mostra o nome e o número de ID do thread para cada thread parado. Nesse caso, há apenas um thread, cujo nome é provavelmente `<noname>`.  

    > [!TIP]
    > Você talvez ache útil identificar threads sem nome ao renomeá-las. Na janela Threads, escolha **renomeie** após o botão direito do mouse no **nome** coluna na linha de thread.
  
4.  Clique com botão direito no marcador de thread para ver as opções disponíveis no menu de atalho. 
    
  
## <a name="flagging-and-unflagging-threads"></a>Sinalizando e removendo a sinalização de threads  
Você pode sinalizar os threads que você deseja dar atenção especial. Sinalizar threads é uma boa maneira de manter o controle de threads importantes e ignorar threads que você não se importa.  
  
#### <a name="to-flag-threads"></a>Para sinalizar threads   

1.  Na **modo de exibição** , aponte para **barras de ferramentas**.  
  
    Certifique-se de que o **local de depuração** barra de ferramentas está selecionada.

2.  Vá para o **local de depuração** barra de ferramentas e clique no **Thread** lista.  
  
    > [!NOTE]
    >  Você pode reconhecer essa barra de ferramentas por três listas importantes: **processo**, **Thread**, e **quadro de pilha**.  
  
3.  Observe quantos threads aparecem na lista.  
  
4.  Volte ao editor de código fonte e com o botão direito no marcador de thread ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") novamente.  
  
5.  No menu de atalho, aponte para **sinalizador**e, em seguida, clique no nome do thread e o número de ID.  
  
6.  Volte para **local de depuração** barra de ferramentas e localizar o **Mostrar somente Threads sinalizados** ícone ![Mostrar Threads sinalizados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker") para o à direita do **Thread** lista.  
  
    O ícone de sinalizadores no botão estava esmaecido antes. Agora, ele é um botão de Active Directory.  
  
7.  Clique o **Mostrar somente Threads sinalizados** ícone.  
  
    Somente o thread sinalizado agora aparece na lista. (Você pode clicar no botão de sinalizador único para voltar ao **Mostrar todos os Threads** modo.)

8. Abra a janela Threads escolhendo **Depurar > Windows > Threads**.

    ![Janela Threads](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    No **Threads** janela, o thread sinalizado possui um ícone de sinalizador de vermelho destacado anexado a ele.

    > [!TIP]
    > Quando você sinalizou alguns threads, pode ser uma linha de código no editor de códigos com o botão direito e escolha **executar Threads sinalizados Cursor** (certifique-se de que você escolha entrará em todos os threads sinalizados de código). Isso irá pausar threads na linha selecionada de código, tornando mais fácil controlar a ordem de execução pelo [congelando e Descongelando threads](#bkmk_freeze).
  
11. No editor de código fonte, clique com botão direito no marcador de thread novamente.  
  
     Observe quais opções estão disponíveis no menu de atalho. Em vez de **sinalizador**, você agora verá **Remover sinalização**. Não clique **Remover sinalização**.  

     Para descobrir como a sinalização do thread, vá para o próximo procedimento.  
  
#### <a name="to-unflag-threads"></a>Para remover a sinalização de threads  
  
1.  No **Threads** janela, clique na linha correspondente ao thread sinalizado.  
  
     Um menu de atalho é exibido. Ele tem opções para **Remover sinalização** e **Remover sinalização de todos os Threads**.  
  
2.  Para remover a sinalização do thread, clique em **Remover sinalização**.  

    Examine os **local de depuração** barra de ferramentas novamente. O **Mostrar somente Threads sinalizados** botão ficará esmaecido novamente. Você removerá a sinalização do único thread sinalizado. Como não há nenhum thread sinalizado, a barra de ferramentas voltou para **Mostrar todos os Threads** modo. Clique o **Thread** listar e verificar que você pode ver todos os threads.  
  
5.  Volte para o **Threads** janela e examinar as colunas de informações.  
  
    A primeira coluna, você observará um ícone de sinalizador de estrutura de tópicos em cada linha da lista de threads. (O contorno significa que o thread é sem sinalização.)  
  
6.  Clique nos ícones de estrutura de tópicos do sinalizador para dois threads, o segundo e terceiro da parte inferior da lista. 

    Os ícones de sinalizador ficam vermelho contínuo, em vez de contornos vazado.  
  
7.  Clique no botão na parte superior da coluna do sinalizador.  
  
    A ordem da lista de thread foi alterada quando você clicou no botão. A lista de thread agora é classificada com os threads sinalizados na parte superior.  
  
8.  Novamente, clique no botão na parte superior da coluna do sinalizador.  
  
    A ordem de classificação foi modificada novamente.  
  
## <a name="more-about-the-threads-window"></a>Mais sobre a janela de threads  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Para saber mais sobre a janela de threads  
  
1.  No **Threads** janela, examine a terceira coluna da esquerda. O botão na parte superior desta coluna diz **ID**.  
  
2.  Clique em **ID**.  
  
     A lista de thread agora é classificada pelo número de identificação do thread.  
  
3.  Clique com o botão direito em qualquer thread na lista. No menu de atalho, clique em **exibição Hexadecimal**.  
  
     O formato dos números da ID de thread é alterado.  
  
4.  Focalize o ponteiro do mouse sobre o **local** coluna para qualquer thread na lista.  
  
     Depois de um atraso momentâneo, um DataTip é exibido. Ele mostra uma pilha de chamadas parcial para o thread.

     > [!TIP]
     > Para obter uma exibição gráfica das pilhas de chamada para threads, abra o [pilhas paralelas](../debugger/using-the-parallel-stacks-window.md) janela (durante a depuração, escolha **depurar / Windows / pilhas paralelas**).  
  
5.  Examine a quarta coluna da esquerda, que é rotulada **categoria**. Os threads são classificados em categorias.  
  
     O primeiro thread criado em um processo é chamado de thread principal. Localize-o na lista de thread.  
  
6.  O thread principal com o botão direito e, em seguida, clique em **alternar para Thread**.  
  
     Um **modo de interrupção** janela é exibida. Ele informa que o depurador não está executando qualquer código que ele possa exibir (porque o thread principal).   
  
7.  Examine os **pilha de chamadas** janela e o **local de depuração** barra de ferramentas.  
  
     O conteúdo a **pilha de chamadas** janela foram alterados. 

## <a name="bkmk_freeze"></a> Congelando e Descongelando a execução do thread 

Você pode congelar e descongelar (suspender e retomar) threads para controlar a ordem na qual threads executam o trabalho. Isso pode ajudá-lo a resolver problemas de simultaneidade, como deadlocks e condições de corrida.

> [!TIP]
> Se você quiser seguir um único thread sem congelamento de outros threads (também um depuração cenário comum), consulte [começar a depurar aplicativos multissegmentados](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para congelar e descongelar threads  
  
1.  No **Threads** janela, clique em qualquer thread e, em seguida, clique em **congelar**.  
  
2.  Examine a segunda coluna (a coluna atual do thread). O ícone de pausa agora aparece ali. Esses ícone de pausa indica que o thread está congelado.  
  
3.  Mostrar o **contagem suspensa** coluna, selecionando-o na **colunas** lista.

    A contagem de suspensão para o thread agora é 1.  
  
4.  Clique com botão direito no thread congelado e, em seguida, clique em **descongelar**.  
  
     A coluna de thread atual e o **contagem suspensa** alteração de coluna. 
  
## <a name="switching-the-to-another-thread"></a>Alternando o para outro thread 
  
#### <a name="to-switch-threads"></a>Para alternar segmentos  
  
1.  No **Threads** janela, examine a segunda coluna da esquerda (a coluna atual do thread). O botão na parte superior dessa coluna não tem texto ou ícone.
  
2.  Examine a coluna atual do thread e observe que um thread tem uma seta amarela. A seta amarela indica que esse thread é o thread atual (esse é o local atual do ponteiro de execução).
  
    Anote o número de ID do thread no qual você pode ver o ícone de thread atual. Você moverá o ícone de thread atual para outro thread, mas você terá que colocá-lo novamente quando terminar. 
  
3.  Outro thread com o botão direito e, em seguida, clique em **alternar para Thread**.  
  
4.  Examine os **pilha de chamadas** janela no editor de código fonte. O conteúdo foi alterado.  
  
5.  Examine os **local de depuração** barra de ferramentas. O ícone de thread atual foi alterado lá também.  
  
6.  Vá para o **local de depuração** barra de ferramentas. Selecione um thread diferente de **Thread** lista.  
  
7.  Examine os **Threads** janela. O ícone de thread atual foi alterado.  
  
8. No editor de código fonte, clique com botão direito um marcador de thread. No menu de atalho, aponte para **alternar para Thread** e clique em um número de nome/ID do thread.  
  
     Agora você já viu três maneiras de alterar o ícone de thread atual para outro thread: usando o **Threads** janela, o **Thread** listar no **local de depuração** barra de ferramentas e o marcador de thread no editor de código fonte.  
  
     Com o marcador de thread, você pode alternar somente para threads que pararam nesse local específico. Usando o **Threads** janela e **local de depuração** barra de ferramentas, você pode alternar para qualquer thread.   
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como mudar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)
