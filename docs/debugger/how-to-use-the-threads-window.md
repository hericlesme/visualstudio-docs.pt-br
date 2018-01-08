---
title: Depurar um aplicativo multithread usando a janela Threads | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 253798cdde2a40a70496dbe2ed89f9d0a9316640
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2018
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>Passo a passo: Depurar um aplicativo multithread no Visual Studio usando a janela Threads
O Visual Studio fornece um **Threads** elementos para ajudá-lo a depurar aplicativos multithread de interface de janela e outro usuário. Este tutorial mostra como usar o **Threads** janela e **local do depurador** barra de ferramentas. Para obter informações sobre outras ferramentas, consulte [começar a depurar aplicativos multithread](../debugger/get-started-debugging-multithreaded-apps.md). Este tutorial leva apenas alguns minutos, mas concluí-la irá familiarizá-lo com os recursos para depurar aplicativos multithread.   
  
Para iniciar este tutorial, você precisa de um projeto de aplicativo multi-threaded. Siga as etapas listadas aqui para criar o projeto.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Para criar o projeto de aplicativo multithread  
  
1.  Sobre o **arquivo** menu, escolha **novo** e, em seguida, clique em **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  No **tipo de projeto**s caixa, clique no idioma de sua escolha: **Visual Basic**, **Visual C#**, ou **Visual C++**.  
  
3.  No **modelos** caixa, escolha **aplicativo de Console**.  
  
4.  No **nome** caixa, digite o nome MyThreadWalkthroughApp.  
  
5.  Clique em **OK**.  
  
     Um novo projeto de console é exibido. Quando o projeto tiver sido criado, um arquivo de origem aparecerá. Dependendo da linguagem escolhida, o arquivo de origem poderá ser chamado Module1.vb, Program.cs ou MyThreadWalkthroughApp.cpp  
  
6.  Excluir o código que aparece no arquivo de origem e substitua-o com o código de exemplo que aparece na seção "Criar um segmento" do tópico [criando Threads e passando dados na hora de início](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time).  
  
7.  Sobre o **arquivo** menu, clique em **Salvar tudo**.  
  
#### <a name="to-begin-the-tutorial"></a>Para começar o tutorial  
  
-   No editor de código fonte, procure o seguinte código:  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine()
    ```  
  
    ```CSharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>Para iniciar a depuração  
  
1.  Clique na medianiz esquerda do `Console.WriteLine` instrução para inserir um novo ponto de interrupção.  
  
     Na medianiz no lado esquerdo do editor de código fonte, um círculo vermelho é exibido. Isso indica que um ponto de interrupção agora está definido nesse local.  
  
2.  Sobre o **depurar** menu, clique em **iniciar depuração** (**F5**).  
  
     A depuração é iniciada, seu aplicativo de console começa a ser executado e, em seguida, para no ponto de interrupção.  
  
3.  Se a janela do aplicativo de console tiver o foco neste momento, clique na janela do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para retornar o foco para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  No editor de código fonte, localize a linha que contém o código a seguir:  
  
    ```VB  
    Thread.Sleep(5000)   
    ```  
  
    ```CSharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```
  
#### <a name="to-discover-the-thread-marker"></a>Para descobrir o marcador de thread  

1.  Na barra de ferramentas Depurar, clique o **Mostrar Threads na origem** botão ![Mostrar Threads na origem](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker"). 
  
2.  Examine a medianiz no lado esquerdo da janela. Nessa linha, você verá um *marcador de thread* ícone ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") que se parece com dois threads pano. O marcador de thread indica que um thread está parado nesse local.  
  
3.  Passe o ponteiro sobre o marcador de thread. Um DataTip aparece. O DataTip mostra o nome e o número de ID do thread para cada thread parado. Nesse caso, há apenas um thread, cujo nome é provavelmente `<noname>`.  

    > [!TIP]
    > Talvez seja útil para identificar threads sem nome renomeando-los. Na janela de Threads, escolha **Renomear** depois de clicar duas vezes no **nome** coluna na linha de thread.
  
4.  Clique no marcador de thread para ver as opções disponíveis no menu de atalho. 
    
  
## <a name="flagging-and-unflagging-threads"></a>Sinalizando e removendo a sinalização de threads  
Você pode sinalizar threads para dar atenção especial. Sinalizar threads é uma boa maneira de controlar os threads importantes e ignorar threads que não faz sobre.  
  
#### <a name="to-flag-threads"></a>Para sinalizar threads   

1.  Em **exibição** , aponte para **barras de ferramentas**.  
  
    Verifique se o **local do depurador** barra de ferramentas está selecionada.

2.  Vá para o **local do depurador** barra de ferramentas e clique no **Thread** lista.  
  
    > [!NOTE]
    >  Você pode reconhecer essa barra de ferramentas por três listas proeminentes: **processo**, **Thread**, e **quadro de pilhas**.  
  
3.  Observe quantos threads aparecem na lista.  
  
4.  Volte para o editor de código fonte e clique no marcador de thread ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") novamente.  
  
5.  No menu de atalho, aponte para **sinalizador**e, em seguida, clique no nome do thread e o número de identificação.  
  
6.  Volte para **depuração local** barra de ferramentas e localizar o **Mostrar somente Threads sinalizados** ícone ![Mostrar Threads sinalizados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker") para o à direita do **Thread** lista.  
  
    O ícone de sinalizadores no botão foi esmaecido antes. Agora, é um botão de ativo.  
  
7.  Clique o **Mostrar somente Threads sinalizados** ícone.  
  
    Somente o thread sinalizado agora aparece na lista. (Você pode clicar no botão de único sinalizador para voltar ao **Mostrar todos os Threads** modo.)

8. Abra a janela Threads escolhendo **Depurar > Windows > Threads**.

    ![Janela Threads](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    No **Threads** janela, o thread sinalizado possui um ícone de sinalizador de vermelho proeminentes anexado a ele.

    > [!TIP]
    > Quando você sinalizou alguns threads, você pode clique uma linha de código no editor de código e escolha **executar Threads sinalizados Cursor** (certifique-se de que você escolha o código que todos os threads sinalizados alcançará). Isso irá pausar threads na linha selecionada de código, tornando mais fácil controlar a ordem de execução pelo [congelar e descongelar threads](#bkmk_freeze).
  
11. No editor de código fonte, clique no marcador de thread novamente.  
  
     Observe quais opções estão disponíveis no menu de atalho. Em vez de **sinalizador**, você agora veja **Unflag**. Não clique **Unflag**.  

     Para saber como sinalizar threads, vá para o próximo procedimento.  
  
#### <a name="to-unflag-threads"></a>Para remover a sinalização de threads  
  
1.  No **Threads** janela, clique na linha correspondente para o thread sinalizado.  
  
     Um menu de atalho é exibido. Ele tem opções para **Unflag** e **Remover Sinalizador de todos os Threads**.  
  
2.  Para remover o sinalizador de thread, clique em **Unflag**.  

    Examine o **depuração local** barra de ferramentas novamente. O **Mostrar somente Threads sinalizados** botão fica esmaecido novamente. Você removerá a sinalização do único thread sinalizado. Como não há nenhum thread sinalizado, a barra de ferramentas ficou novamente para **Mostrar todos os Threads** modo. Clique o **Thread** lista e verifique se que você pode ver todos os threads.  
  
5.  Volte para o **Threads** janela e examinar as colunas de informações.  
  
    A primeira coluna, você observará um ícone de sinalizador de estrutura de tópicos em cada linha da lista de threads. (A estrutura de tópicos significa que o thread está sem sinalizador).  
  
6.  Clique nos ícones de estrutura de tópicos do sinalizador para dois threads, o segundo e terceiro na parte inferior da lista. 

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
  
4.  Passe o ponteiro do mouse sobre o **local** coluna para qualquer thread na lista.  
  
     Depois de um atraso momentâneo, um DataTip é exibido. Ele mostra uma pilha de chamadas parcial para o thread.

     > [!TIP]
     > Para obter uma exibição gráfica de pilhas de chamadas de threads, abra o [pilhas paralelas](../debugger/using-the-parallel-stacks-window.md) janela (durante a depuração, escolha **depurar / Windows / pilhas paralelas**).  
  
5.  Examine a quarta coluna da esquerda, que é rotulada **categoria**. Os threads são classificados em categorias.  
  
     O primeiro thread criado em um processo é chamado de thread principal. Localize-o na lista de thread.  
  
6.  Clique com botão direito do thread principal e, em seguida, clique em **alternar para Thread**.  
  
     Um **modo de interrupção** janela é exibida. Indica que o depurador não está executando qualquer código que pode exibir (porque o thread principal).   
  
7.  Examine o **pilha de chamadas** janela e **local do depurador** barra de ferramentas.  
  
     O conteúdo do **pilha de chamadas** janela foram alterados. 

## <a name="bkmk_freeze"></a>Congelar e descongelar a execução do thread 

Você pode congelar e descongelar (suspender e retomar) threads para controlar a ordem na qual os threads executam trabalho. Isso pode ajudá-lo a resolver problemas de simultaneidade, como deadlocks e condições de corrida.

> [!TIP]
> Se você quiser seguir um único thread sem congelamento de outros threads (também um depuração cenário comum), consulte [começar a depurar aplicativos multithread](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para congelar e descongelar threads  
  
1.  No **Threads** janela, clique em qualquer thread e, em seguida, clique em **congelar**.  
  
2.  Examine a segunda coluna (a coluna atual do thread). O ícone de pausar agora aparece nele. Esses pausar indica que o thread está congelado.  
  
3.  Mostrar o **suspenso contagem** coluna selecionando-na **colunas** lista.

    A contagem de suspensão para o thread agora é 1.  
  
4.  Clique o thread congelado e, em seguida, clique em **descongelar**.  
  
     A coluna do thread atual e o **suspenso contagem** alteração de coluna. 
  
## <a name="switching-the-to-another-thread"></a>Alternar o para outro thread 
  
#### <a name="to-switch-threads"></a>Para alternar segmentos  
  
1.  No **Threads** janela, examine a segunda coluna da esquerda (a coluna atual do thread). O botão na parte superior dessa coluna não tem texto ou ícone.
  
2.  Examine a coluna atual do thread e observe que um thread tem uma seta amarela. A seta amarela indica que esse thread é o thread atual (esse é o local atual do ponteiro de execução).
  
    Anote o número de identificação do thread em que você pode ver o ícone do thread atual. Você moverá o ícone do thread atual para outro thread, mas será necessário colocá-lo novamente quando terminar. 
  
3.  Clique em outro thread e, em seguida, clique em **alternar para Thread**.  
  
4.  Examine o **pilha de chamadas** janela no editor de código fonte. O conteúdo foi alterado.  
  
5.  Examine o **local do depurador** barra de ferramentas. O ícone de thread atual foi alterado, muito.  
  
6.  Vá para o **local do depurador** barra de ferramentas. Selecione um thread diferente do **Thread** lista.  
  
7.  Examine o **Threads** janela. O ícone de thread atual foi alterado.  
  
8. No editor de código fonte, clique em um marcador de thread. No menu de atalho, aponte para **alternar para Thread** e clique em um número de identificação do nome do thread.  
  
     Agora você já viu três maneiras de alterar o ícone do thread atual para outro thread: usando o **Threads** janela, o **Thread** lista o **local do depurador** barra de ferramentas e o marcador de thread no editor de código fonte.  
  
     Com o marcador de thread, você pode alternar somente para threads que são interrompidos nesse local específico. Usando o **Threads** janela e **local do depurador** barra de ferramentas, você pode alternar para qualquer thread.   
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como mudar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)
