---
title: Exibir Threads do depurador | Microsoft Docs
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bde9f1c8aa09f8e5961bd228a5f1947c2fc30f82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="view-threads-in-the-debugger-in-visual-studio-using-the-threads-window"></a>Exibir Threads do depurador no Visual Studio usando a janela Threads
No **Threads** janela, você pode examinar e trabalhar com os threads do aplicativo que você está depurando. Para obter orientação passo a passo sobre como usar o **Threads** janela, consulte [passo a passo: depurar usando a janela Threads](../debugger/how-to-use-the-threads-window.md).
  
 O **Threads** janela contém uma tabela em que cada linha representa um segmento em seu aplicativo. Por padrão, a tabela lista todos os threads em seu aplicativo, mas você pode filtrar a lista para mostrar apenas os threads do seu interesse. Cada coluna contém um tipo diferente de informação. Você também pode ocultar algumas colunas. Se você exibir todas as colunas, as seguintes informações são exibidas, da esquerda para a direita:  
  
-   A coluna do sinalizador, em que você pode marcar um thread para o qual você deseja prestar atenção especial. Para obter informações sobre como um thread do sinalizador, consulte [como: sinalizador e sinalizar Threads](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   A coluna de segmento atual, no qual uma seta amarela indica que o thread atual (uma estrutura de tópicos de seta indica o contexto do depurador atual por um thread não atual).
  
-   O **ID** coluna, que contém o número de identificação para cada thread.  
  
-   O **ID gerenciado** coluna, que contém os números de identificação de gerenciado para threads gerenciados.  
  
-   O **categoria** coluna, que categoriza threads como threads de interface do usuário, manipuladores de chamada de procedimento remoto ou threads de trabalho. Uma categoria especial identifica o thread principal do aplicativo.  
  
-   O **nome** coluna, que identificam cada thread por nome, se houver, ou como \<sem nome >.  
  
-   O **local** coluna, que mostra onde o thread está em execução. Você pode expandir este local para mostrar a pilha de chamadas inteira para o thread.  
  
-   O **prioridade** coluna, que contém a prioridade ou precedência que o sistema atribuído a cada thread.  
  
-   O **máscara de afinidade** coluna, que é uma coluna avançada (geralmente ocultada). Esta coluna mostra a máscara de afinidade do processador para cada thread. Em um sistema com vários processadores, a máscara de afinidade determina quais processadores em qual thread pode ser executado.  
  
-   O **suspenso contagem** coluna (normalmente ocultada), que contém a contagem suspensa e normalmente é oculto. Esta contagem determina se um thread pode ser executado. Para obter uma explicação de contagem suspensa, consulte “Congelando e descongelando threads” posteriormente neste tópico.  
  
-   O **nome do processo** coluna (normalmente ocultada), que contém o processo ao qual pertence cada thread. Esta coluna pode ser útil quando você estiver depurando vários processos.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Para exibir a janela de threads no modo de interrupção ou no modo de execução  
  
-   Durante a depuração, selecione o **depurar** , aponte para **Windows**e, em seguida, clique em **Threads**.  
  
### <a name="to-display-or-hide-a-column"></a>Para exibir ou ocultar uma coluna  
  
-   Na barra de ferramentas na parte superior do **Threads** janela, clique em **colunas**, em seguida, marque ou desmarque o nome da coluna que você deseja exibir ou ocultar.    

## <a name="display-flagged-threads"></a>Exibir Threads sinalizados  
 Você pode sinalizar um thread que você deseja dar atenção especial, marcando-o com um ícone de **Threads** janela. Para obter mais informações, consulte [como: sinalizador e sinalizar Threads](../debugger/how-to-flag-and-unflag-threads.md). No **Threads** janela você pode optar por exibir todos os threads ou apenas os threads sinalizados.  
  
#### <a name="to-display-only-flagged-threads"></a>Para exibir somente threads sinalizados  
  
-   Escolha o **Mostrar somente Threads sinalizados** botão na parte superior do **Threads** janela. (Se ele estiver esmaecido, você precisa sinalizar alguns segmentos primeiro.) 

## <a name="freeze-and-thaw-threads"></a>Congelar e descongelar Threads  
 Quando você congela um thread, o sistema não iniciará a execução do thread mesmo se os recursos estiverem disponíveis.  
  
 No código nativo, você pode suspender ou retomar threads chamando as funções do Windows `SuspendThread` e `ResumeThread` ou as funções MFC [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class.md#cwinthread__suspendthread) e [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class.md#cwinthread__resumethread). Se você chamar `SuspendThread` ou `ResumeThread`, você alterar o *suspenso contagem*, que aparece no **Threads** janela. Porém, se você congelar ou descongelar um thread nativo, não alterará a contagem suspensa. No código nativo, um thread não pode ser executado a menos que seja descongelado e tenha uma contagem suspensa de zero.  
  
 No código gerenciado, congelar ou descongelar um thread altera a contagem suspensa. No código gerenciado, um thread congelado tem uma contagem suspensa de 1. No código nativo, um thread congelado tem uma contagem suspensa de 0 a menos que o thread tenha sido suspenso por uma chamada `SuspendThread`.  
  
> [!NOTE]
>  Quando você depura uma chamada de código nativo para o código gerenciado, o código gerenciado é executado no mesmo thread físico que o código nativo que o chamou. Suspender ou congelar o thread nativo também congela o código gerenciado.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Para congelar ou descongelar a execução de um thread  
  
-   Na barra de ferramentas na parte superior do **Threads** janela, clique em **congelar Threads** ou **descongelar Threads**.  
  
     Esta ação afeta apenas os threads que são selecionados no **Threads** janela. 

### <a name="switch-to-another-thread"></a>Alternar para outro thread 

Uma seta amarela indica que o thread atual (e o local do ponteiro de execução). Uma seta verde com uma chave final indica que um thread atual não tem o contexto atual do depurador.

#### <a name="to-switch-to-another-thread"></a>Para alternar para outro thread  
  
-   Execute uma das seguintes etapas:  
  
    -   Clique duas vezes em qualquer thread.  
  
    -   Um thread de mouse e clique em **alternar para Thread**.

## <a name="group-and-sort-threads"></a>Threads de classificação e de grupo  
 Quando você agrupa threads, um título aparece na tabela para cada grupo. O título contém uma descrição do grupo, como “Thread de trabalho” ou “Threads sem sinalização” e um controle de árvore. Os threads de membro de cada grupo aparecem no cabeçalho do grupo. Se você quiser ocultar os threads de membro para um grupo, poderá usar o controle de árvore para recolher o grupo.  
  
 Como o agrupamento tem precedência sobre a classificação, você poderá agrupar threads por categoria, por exemplo, e, em seguida, classificá-los por ID dentro de cada categoria.  
  
#### <a name="to-sort-threads"></a>Para classificar threads  
  
1.  Na barra de ferramentas na parte superior do **Threads** janela, clique no botão na parte superior de qualquer coluna.  
  
     Os threads agora são classificados pelos valores nessa coluna.  
  
2.  Se você quiser inverter a ordem de classificação, clique no mesmo botão novamente.  
  
     Os threads que apareceram na parte superior da lista agora aparecem na parte inferior.  
  
#### <a name="to-group-threads"></a>Para agrupar threads  
  
-   No **Threads** de ferramentas da janela, clique no **Agrupar por** lista e clique nos critérios que você deseja threads de grupo por.  
  
#### <a name="to-sort-threads-within-groups"></a>Para classificar threads dentro de grupos  
  
1.  Na barra de ferramentas na parte superior do **Threads** janela, clique no **Agrupar por** lista e clique nos critérios que você deseja threads de grupo por.  
  
2.  No **Threads** janela, clique no botão na parte superior de qualquer coluna.  
  
     Os threads agora são classificados pelos valores nessa coluna.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Para expandir ou recolher todos os grupos  
  
-   Na barra de ferramentas na parte superior do **Threads** janela, clique em **expandir grupos** ou **recolher grupos**.  
  
## <a name="search-for-specific-threads"></a>Pesquise a Threads específicos  
 No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], você pode procurar threads que correspondem a uma cadeia de caracteres especificada. Quando você procura por threads no **Threads** janela, a janela exibe todos os threads que correspondem a cadeia de caracteres de pesquisa em qualquer coluna. As informações incluem o local de thread que aparece na parte superior da pilha de chamadas no **local** coluna. Por padrão, no entanto, a pilha de chamadas completa não será pesquisada.  
  
#### <a name="to-search-for-specific-threads"></a>Para pesquisar threads específicos  
  
-   Na barra de ferramentas na parte superior de **Threads** janela, vá para o **pesquisa** caixa e:  
  
    -   Digite uma cadeia de caracteres de pesquisa e pressione ENTER.  
  
         \- ou -  
  
    -   Clique na lista suspensa ao lado de **pesquisa** caixa e selecione uma cadeia de caracteres de pesquisa de uma pesquisa anterior.  
  
-   (Opcional) Para incluir a pilha de chamadas completa em sua pesquisa, selecione **a pilha de chamadas de pesquisa**.   
  
## <a name="display-thread-call-stacks-and-switching-between-frames"></a>Exibir as pilhas de chamadas do Thread e alternar entre os quadros  
Em um programa de vários threads, cada thread tem sua própria pilha de chamadas. O **Threads** janela fornece uma maneira conveniente de exibir essas pilhas.

> [!TIP]
> Para obter uma representação visual da pilha de chamadas para cada thread, use o [pilhas paralelas](../debugger/get-started-debugging-multithreaded-apps.md) janela.
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Para exibir a pilha de chamadas de um thread  
  
-   No **local** coluna, clique no triângulo invertido perto da localização do thread.  
  
     O local é expandido para mostrar a pilha de chamadas para o thread.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Para exibir ou recolher as chamadas de pilhas de todos os threads  
  
-   Na barra de ferramentas na parte superior do **Threads** janela, clique em **expanda pilhas de chamadas** ou **pilhas de chamadas de recolher**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Começar a depuração de um aplicativo multithread](../debugger/get-started-debugging-multithreaded-apps.md)