---
title: 'Passo a passo: Depurando um aplicativo paralelo | Microsoft Docs'
ms.custom: H1HackMay2017
ms.date: 03/22/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aceeb00f81bb858b1cebe19168b7366f08562745
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio"></a>Passo a passo: Depurando um aplicativo paralelo no Visual Studio
Este passo a passo mostra como usar o **tarefas paralelas** e **pilhas paralelas** windows para depurar um aplicativo em paralelo. Essas janelas ajudarão a compreender e verificar o comportamento de tempo de execução de código que usa o [tarefa TPL (biblioteca paralela)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) ou [tempo de execução de simultaneidade](/cpp/parallel/concrt/concurrency-runtime). Este passo a passo fornece código de exemplo que tem pontos de interrupção internos. Depois que o código for interrompida, o passo a passo mostra como usar o **tarefas paralelas** e **pilhas paralelas** windows para examiná-lo.  
  
 Este passo a passo ensina estas tarefas:  
  
-   Como exibir as chamadas de pilhas de todos os threads em uma exibição.  
  
-   Como exibir a lista de instâncias de `System.Threading.Tasks.Task` que são criadas no seu aplicativo.  
  
-   Como exibir as chamadas de pilhas de tarefas reais em vez de threads.  
  
-   Como navegar até o código a partir de **tarefas paralelas** e **pilhas paralelas** windows.  
  
-   Como as janelas lidam com a escala por agrupamento, zoom e outros recursos relacionados.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este passo a passo pressupõe que **Just My Code** está habilitada (ela é habilitada por padrão em versões mais recentes do Visual Studio). No **ferramentas** menu, clique em **opções**, expanda o **depuração** nó, selecione **geral**e, em seguida, selecione **habilitar Apenas meu código (somente gerenciado)**. Se você não definir esse recurso, ainda poderá usar este passo a passo, mas os resultados poderão ser diferentes das ilustrações.  
  
## <a name="c-sample"></a>Exemplo do C#  
 Se você usar o exemplo do C#, este passo a passo também pressuporá que o código externo está oculto. Para ativar o código externo é exibido, clique com botão direito do **nome** cabeçalho da tabela do **pilha de chamadas** janela e depois marque ou desmarque **Mostrar código externo**. Se você não definir esse recurso, ainda poderá usar este passo a passo, mas os resultados poderão ser diferentes das ilustrações.  
  
## <a name="c-sample"></a>Exemplo do C++  
 Se você usar o exemplo do C++, poderá ignorar referências ao código externo neste tópico. O código externo aplica-se somente ao exemplo do C#.  
  
## <a name="illustrations"></a>Ilustrações  
 As ilustrações neste tópico foram gravadas em um computador de quatro núcleos executando o exemplo do C#. Embora você possa usar outras configurações para concluir este passo a passo, as ilustrações poderão diferir do que é exibido em seu computador.  
  
## <a name="creating-the-sample-project"></a>Criando o projeto de exemplo  
 O código de exemplo neste passo a passo é para um aplicativo que não faça nada. O objetivo é apenas entender como usar as janelas de ferramenta para depurar um aplicativo paralelo.  
  
#### <a name="to-create-the-sample-project"></a>Para criar o projeto de exemplo  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
2.  No **modelos instalados** painel, selecione Visual c#, Visual Basic ou Visual C++. Para as linguagens gerenciadas, certifique-se de que [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] seja exibido na caixa da estrutura.  
  
3.  Selecione **aplicativo de Console** e, em seguida, clique em **Okey**. Permaneça na configuração de depuração, que é o padrão.  
  
4.  No projeto, abra o arquivo de código .cpp, .cs ou .vb. Exclua o conteúdo para criar um arquivo de código vazio.  
  
5.  Cole o código a seguir para seu idioma escolhido no arquivo de código vazio.  
  
 [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
 [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
 [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]  
  
1.  Sobre o **arquivo** menu, clique em **Salvar tudo**.  
  
2.  Sobre o **criar** menu, clique em **recompilar solução**.  
  
     Observe que há quatro chamadas a `Debugger.Break` (`DebugBreak` no exemplo do C++). Em virtude disso, você não precisa inserir pontos de interrupção; a execução do aplicativo causará sua interrupção no depurador até quatro vezes.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Usando a janela Pilhas Paralelas: exibição de Threads  
 No menu **Depuração**, clique em **Iniciar Depuração**. Aguarde até que o primeiro ponto de interrupção seja atingido.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Para exibir a pilha de chamadas de um único thread  
  
1.  Sobre o **depurar** , aponte para **Windows** e, em seguida, clique em **Threads**. Encaixe o **Threads** janela na parte inferior do Visual Studio.  
  
2.  Sobre o **depurar** , aponte para **Windows** e, em seguida, clique em **pilha de chamadas**. Encaixe o **pilha de chamadas** janela na parte inferior do Visual Studio.  
  
3.  Clique duas vezes em um thread no **Threads** janela para torná-lo atual. Os threads atuais têm uma seta amarela. Quando você altera o thread atual, sua pilha de chamada é exibida no **pilha de chamadas** janela.  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>Para examinar a janela Pilhas Paralelas  
  
1.  Sobre o **depurar** , aponte para **Windows** e, em seguida, clique em **pilhas paralelas**. Verifique se **Threads** está selecionado na caixa no canto superior esquerdo.  
  
     Usando o **pilhas paralelas** janela, você pode exibir várias pilhas de chamadas ao mesmo tempo em uma exibição. A ilustração a seguir mostra o **pilhas paralelas** acima da janela de **pilha de chamadas** janela.  
  
     ![Threads de exibição na janela pilhas paralelas](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")  
  
     A pilha de chamadas do thread principal é exibida em uma caixa e as pilhas de chamadas dos outros quatro threads são agrupadas em outra caixa. Quatro threads são agrupados porque os quadros de pilhas compartilham os mesmos contextos do método; isto é, estão nos mesmos métodos: `A`, `B`, e `C`. Para exibir as IDs de thread e os nomes dos threads que compartilham a mesma caixa, passe o mouse sobre a caixa com o cabeçalho (**4 Threads**). O segmento atual é exibido em negrito.  
  
     ![Dica de ferramenta que mostra os nomes e IDs de segmento](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")  
  
     A seta amarela indica o quadro de pilhas do thread atual.
  
     Você pode definir os detalhes para mostrar para os quadros de pilha (**nomes de módulo**, **tipos de parâmetro**, **nomes de parâmetro**, **valores de parâmetro**, **Números de linha** e **deslocamentos de Byte**) clicando no **pilha de chamadas** janela.  
  
     Um realce azul ao redor de uma caixa indica que o thread atual é parte dessa caixa. O thread atual também é indicado pelo registro de ativação em negrito na dica de ferramenta. Se você clicar duas vezes o thread principal na janela de Threads, você pode observar que o realce azul no **pilhas paralelas** janela é movida adequadamente.  
  
     ![Realçado thread principal na janela pilhas paralelas](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Para retomar a execução até o segundo ponto de interrupção  
  
1.  Para retomar a execução até que o segundo ponto de interrupção é atingido, no **depurar** menu, clique em **continuar**. A ilustração a seguir mostra a árvore do thread no segundo ponto de interrupção.  
  
     ![Janela pilhas paralelas com muitas ramificações](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")  
  
     No primeiro ponto de interrupção, quatro threads foram de S.A para S.B até o método S.C. Que informações ainda estão visíveis no **pilhas paralelas** janela, mas os quatro threads têm progrediu adicional. Um deles continuou até S.D e depois S.E. Outro continuou até S.F, S.G e S.H. Dois outros continuaram até S.I e S.J, e um deles foi até S.K e o outro continuou até o código externo de não usuário.  
  
     Você pode focalizar o cabeçalho da caixa, por exemplo, **1 Thread** ou **2 Threads**para ver a IDs dos threads de thread. Você pode passar o mouse sobre registros de ativação para consultar as IDs de thread e outros detalhes do registro. O realce azul indica o thread atual e a seta amarela indica o registro de ativação ativo do thread atual.  
  
     O ícone de threads pano (interweaved linhas) indicam os quadros de pilha ativa não-circulantes threads. No **pilha de chamadas** janela, clique duas vezes em S.B para alternar quadros. O **pilhas paralelas** janela indica que o quadro de pilhas atual do thread atual usando um ícone de seta curvada verde.  
  
     No **Threads** janela, alternar entre threads e observe que o modo de exibição de **pilhas paralelas** janela é atualizada.  
  
     Você pode alternar para outro thread ou para outro quadro de outro thread, usando o menu de atalho a **pilhas paralelas** janela. Por exemplo, clique com botão direito S.J, aponte para **alternar para quadro**e, em seguida, clique em um comando.  
  
     ![Caminho de execução de pilhas paralelas](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")  
  
     Clique com botão direito S.C e aponte para **alternar para quadro**. Um dos comandos tem uma marca de seleção que indica o registro de ativação do thread atual. Você pode alternar para esse registro do mesmo thread (apenas a seta verde se moverá) ou pode alternar para o outro thread (o realce azul também se moverá). A ilustração a seguir mostra o submenu.  
  
     ![Menu pilhas com 2 opções em C, embora J seja atual](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")  
  
     Quando um contexto de método está associado a apenas um registro de ativação, o cabeçalho da caixa exibe **1 Thread** e você pode alternar a ele clicando duas vezes. Se você clicar duas vezes em um contexto de método que tenha mais de 1 registro associado a ele, o menu será exibido automaticamente. Enquanto você passa o mouse sobre os contextos de método, observe o triângulo preto no lado direito. Um clique nesse triângulo também exibe o menu de atalho.  
  
     Para os aplicativos grandes que têm muitos threads, talvez seja conveniente se concentrar apenas em um subconjunto de threads. O **pilhas paralelas** janela pode exibir as pilhas de chamadas somente para threads sinalizados. Para sinalizar threads, use o menu de atalho ou a primeira célula de um thread. 

     Na barra de ferramentas, clique o **Mostrar apenas sinalizados** botão ao lado da caixa de lista.  

     ![Paralelo janela pilhas e dica de ferramenta](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")  

     Agora, somente o thread sinalizado aparece no **pilhas paralelas** janela.
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Para retomar a execução até o terceiro ponto de interrupção  
  
1.  Para retomar a execução até que o terceiro ponto de interrupção é atingido, no **depurar** menu, clique em **continuar**.  
  
     Quando vários threads estão no mesmo método, mas o método não estava no início da pilha de chamadas, ele é exibido em caixas diferentes. Um exemplo no ponto de interrupção atual é S.L, que tem três threads e aparece em três caixas. Clique duas vezes em S.L.  
  
     ![Caminho de execução na janela pilhas paralelas](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")  
  
     Observe que S.L está em negrito nas outras duas caixas para que você possa ver onde mais ele aparece. Se você quiser ver quais quadros chamada S.L e qual quadros chamadas, clique no **Alternar modo de exibição do método** na barra de ferramentas. A ilustração a seguir mostra a exibição de método do **pilhas paralelas** janela.  
  
     ![Modo de exibição na janela pilhas paralelas](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")  
  
     Observe como o diagrama girou no método selecionado e o posicionou em sua própria caixa no meio da exibição. Os receptores e os chamadores aparecem nas partes superior e inferior. Clique o **Alternar modo de exibição de método** botão novamente para deixar esse modo.  
  
     O menu de atalho a **pilhas paralelas** janela também tem as seguintes outros itens.  
  
    -   **Exibição hexadecimal** alterna os números em dicas de ferramenta entre decimal e hexadecimal.  
  
    -   **Configurações de símbolo** abrir as caixas de diálogo correspondente.  
  
    -   **Mostrar Threads na fonte** alterna a exibição de marcadores de thread no código-fonte, que mostra o local de threads em seu código-fonte.
  
    -   **Mostrar código externo** exibe todos os quadros, mesmo se eles não estão no código do usuário. Tente verificar o diagrama se expande para acomodar os registros adicionais (que podem ser escurecidos porque você não tem símbolos para eles).  

2.  No **pilhas paralelas** janela, verifique se o **Autorrolagem para quadro de pilhas atual** na barra de ferramentas está em.  

     Quando houver diagramas grandes e você for para o próximo ponto de interrupção, talvez seja conveniente que o modo de exibição role até o registro de ativação ativo do thread atual; isto é, o thread que atingiu o ponto de interrupção primeiro.
  
3.  Antes de continuar, além de **pilhas paralelas** janela, todo o caminho para a esquerda e o final de rolagem.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Para retomar a execução até o quarto ponto de interrupção  
  
1.  Para retomar a execução até o quarto de interrupção, no **depurar** menu, clique em **continuar**.  
  
     Observe como o modo de exibição rolou automaticamente até o local certo. Alternar os threads no **Threads** switch ou a janela pilha de quadros no **pilha de chamadas** janela e observe como o modo de exibição sempre autoscrolls ao quadro correto. Desativar **Autorrolagem para quadro atual da ferramenta** opção e exibir a diferença.  
  
     O **exibição vista panorâmica** também ajuda com diagramas grandes no **pilhas paralelas** janela. Por padrão, o **exibição vista panorâmica** está em. Mas você pode ativá-lo clicando no botão entre as barras de rolagem no canto inferior direito da janela, conforme mostrado na ilustração a seguir.  
  
     ![Vista&#45;olho exibição na janela pilhas paralelas](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")  
  
     No Vista detalhada, você pode mover o retângulo para deslocar-se rapidamente em torno do diagrama.  
  
     Outra maneira de mover o diagrama em qualquer direção é clicar em uma área em branco do diagrama e arrastá-la até onde desejar.  
  
     Para ampliar ou reduzir o diagrama, mantenha pressionada a tecla CTRL enquanto move a roda do mouse. Como alternativa, clique no botão Aplicar Zoom na barra de ferramentas e use a ferramenta Zoom.  
  
     Você também pode exibir as pilhas em uma direção de cima para baixo, em vez de baixo para cima, clicando o **ferramentas** menu, clique em **opções**e, em seguida, marque ou desmarque a opção sob o **depuração** nó.  
  
2.  Antes de continuar no **depurar** menu, clique em **parar depuração** para terminar a execução.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Usando a janela Tarefas Paralelas e o Modo de Exibição Tarefas na janela Pilhas Paralelas  
 Recomendamos que você conclua os procedimentos anteriores antes de continuar.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Para reiniciar o aplicativo até atingir o primeiro ponto de interrupção  
  
1.  Sobre o **depurar** menu, clique em **iniciar depuração** e aguarde até que o primeiro ponto de interrupção seja atingido.  
  
2.  Sobre o **depurar** , aponte para **Windows** e, em seguida, clique em **Threads**. Encaixe o **Threads** janela na parte inferior do Visual Studio.  
  
3.  Sobre o **depurar** , aponte para **Windows** e clique em **pilha de chamadas**. Encaixe o **pilha de chamadas** janela na parte inferior do Visual Studio.  
  
4.  Clique duas vezes em um thread no **Threads** janela torna atual. Os threads atuais têm a seta amarela. Quando você altera o thread atual, as outras janelas são atualizadas. Em seguida, examinaremos tarefas.  
  
5.  Sobre o **depurar** , aponte para **Windows**e, em seguida, clique em **tarefas**. A ilustração a seguir mostra o **tarefas** janela.  
  
     ![Quatro executando as tarefas na janela tarefas](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")  
  
     Para cada tarefa em execução, você pode ler a ID, que é retornada pela propriedade do mesmo nome, a ID e o nome do thread que a executa, seu local (passar o mouse sobre ele exibe uma dica de ferramenta que tem a pilha de chamadas inteira). Além disso, sob o **tarefa** coluna, você pode ver o método que foi passado para a tarefa; em outras palavras, o ponto inicial.  
  
     Você pode classificar qualquer coluna. Observe o glifo de classificação que indica a coluna e a direção de classificação. Também é possível reorganizar as colunas arrastando-as para a esquerda ou a direita.  
  
     A seta amarela indica a tarefa atual. Você pode alternar tarefas clicando duas vezes em uma tarefa ou usando o menu de atalho. Quando você alterna tarefas, o thread subjacente se torna o atual e as outras janelas são atualizadas.  
  
     Quando você alterna manualmente de uma tarefa para outra, a seta amarela se move, mas uma seta branca ainda mostra a tarefa que causou a interrupção do depurador.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Para retomar a execução até o segundo ponto de interrupção  
  
1.  Para retomar a execução até que o segundo ponto de interrupção é atingido, no **depurar** menu, clique em **continuar**.  
  
     Anteriormente, o **Status** coluna mostrou todas as tarefas como ativo, mas duas das tarefas são bloqueadas. As tarefas podem ser bloqueadas por diversos motivos diferentes. No **Status** coluna, passe o mouse sobre uma tarefa em espera para saber por que ele está bloqueado. Por exemplo, na ilustração, a tarefa 3 está aguardando a tarefa 4.  
  
     ![Duas tarefas em espera na janela de tarefas](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")  
  
     A tarefa 4, por sua vez, está aguardando um monitor de propriedade do thread atribuído à tarefa 2. (A linha de cabeçalho de atalho e escolha **colunas** > **atribuição de Thread** para exibir o valor de atribuição de thread de tarefa 2).
  
     ![Aguardando a dica de ferramenta na janela de tarefas e tarefa](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")
  
     Você pode sinalizar uma tarefa clicando no sinalizador na coluna da primeira a **tarefas** janela.  
  
     Você pode usar a sinalização para acompanhar tarefas entre diferentes pontos de interrupção na sessão de depuração mesmo ou para filtrar as tarefas cujas pilhas de chamadas são mostradas no **pilhas paralelas** janela.  
  
     Quando você usou o **pilhas paralelas** janela anterior, você exibiu os threads do aplicativo. Exibição de **pilhas paralelas** janela novamente, mas desta vez exibir as tarefas do aplicativo. Isso é feito selecionando **tarefas** na caixa na parte superior esquerda. A ilustração a seguir mostra o Modo de Exibição de Tarefas.  
  
     ![Modo de exibição na janela pilhas paralelas tarefas](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")  
  
     Threads que não estão sendo executados tarefas não são mostrados na exibição de tarefas do **pilhas paralelas** janela. Além disso, para os threads que executam tarefas, alguns registros de ativação que não são relevantes para tarefas são filtrados das partes superior e inferior da pilha.  
  
     Exibição de **tarefas** janela novamente. Clique com o botão direito do mouse em qualquer cabeçalho de coluna para ver um menu de atalho da coluna.  
  
     Você pode usar o menu de atalho para adicionar ou remover colunas. Por exemplo, a coluna Appdomain não está selecionada; consequentemente, não é exibida na lista. Clique em **pai**. O **pai** coluna aparece sem valores para qualquer um dos quatro tarefas.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Para retomar a execução até o terceiro ponto de interrupção  
  
1.  Para retomar a execução até que o terceiro ponto de interrupção é atingido, no **depurar** menu, clique em **continuar**.  
  
     Uma nova tarefa, tarefa 5, está sendo executada e a tarefa 4 está aguardando. Você pode ver por que focalizando a tarefa de espera no **Status** janela. No **pai** coluna, observe que a tarefa 4 é o pai da tarefa 5.  
  
     Para visualizar melhor a relação pai-filho, clique com botão direito a linha de cabeçalho de coluna e, em seguida, clique em **exibição pai-filho**. Você verá a ilustração a seguir.  
  
     ![Pai&#45;exibição filho na janela de tarefas](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")  
  
     Observe que tarefas 4 e 5 estão em execução no mesmo thread (Mostrar o **atribuição de Thread** coluna se ele estiver oculto). Essas informações não são exibidas no **Threads** janela; vendo aqui é outro benefício do **tarefas** janela. Para confirmar isso, exibir o **pilhas paralelas** janela. Certifique-se de que você está exibindo **tarefas**. Localize as etapas 4 e 5 clicando duas vezes no **tarefas** janela. Ao fazer isso, o realce azul **pilhas paralelas** janela é atualizada. Você também pode localizar etapas 4 e 5 examinando as dicas de ferramentas sobre o **pilhas paralelas** janela.  
  
     ![Modo de exibição na janela pilhas paralelas tarefa](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")  
  
     No **pilhas paralelas** janela, clique com botão direito S.P e, em seguida, clique em **ir para Thread**. A janela alterna para o Modo de Exibição de Threads e o registro correspondente está na exibição. Você pode ver as duas tarefas no mesmo thread.  
  
     ![Realçado thread na exibição de threads](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")  
  
     Este é outro benefício do modo de exibição tarefas no **pilhas paralelas** janela, em comparação comparada o **Threads** janela.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Para retomar a execução até o quarto ponto de interrupção  
  
1.  Para retomar a execução até que o terceiro ponto de interrupção é atingido, no **depurar** menu, clique em **continuar**. Clique o **ID** cabeçalho de coluna para classificar por ID. Você verá a ilustração a seguir.  
  
     ![Quatro estados na janela pilhas paralelas de tarefas](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")  
  
     Como a tarefa 5 foi concluída, ele não é mais exibida. Se esse não for o caso em seu computador e o bloqueio não é mostrado, etapa uma vez pressionando **F11**.  
  
     Tarefas 3 e 4 agora estão esperando um do outro e são bloqueadas. Também há 5 novas tarefas que são filhos da tarefa 2 e estão agendadas agora. As tarefas agendadas são aquelas iniciadas no código mas que ainda não foram executadas. Portanto, seus **local** e **atribuição de Thread** colunas estão vazias.  
  
     Exibição de **pilhas paralelas** janela novamente. O cabeçalho de cada caixa tem uma dica de ferramenta que mostra as IDs e os nomes de thread. Alternar para modo de exibição de tarefas no **pilhas paralelas** janela. Passe o mouse sobre um cabeçalho para ver o nome, a ID e o status da tarefa, como mostra a ilustração a seguir.  
  
     ![Dica de ferramenta de cabeçalho na janela pilhas paralelas](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")  
  
     Você pode agrupar as tarefas por coluna. No **tarefas** janela, com o botão direito do **Status** cabeçalho de coluna e clique **agrupe por Status**. A ilustração a seguir mostra o **tarefas** janela agrupados por status.  
  
     ![Agrupados tarefas na janela tarefas](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")  
  
     Também é possível agrupar por qualquer outra coluna. Agrupando tarefas, você pode se concentrar em um subconjunto de tarefas. Cada grupo recolhível tem uma contagem de itens que são agrupados.
  
     O último recurso do **tarefas** janela examinar é o menu de atalho que é exibido quando você clica uma tarefa.  
  
     O menu de atalho exibe comandos diferentes, dependendo do status da tarefa. Os comandos podem incluir **cópia**, **Selecionar tudo**, **exibição Hexadecimal**, **alternar para a tarefa**, **congelar atribuído Thread**, **congelar todos os Threads, mas isso**, e **descongelar o Thread atribuído**, e **sinalizador**.  
  
     Você pode congelar o thread subjacente de uma tarefa, ou tarefas, ou pode congelar todos os threads exceto o atribuído. Um thread congelado é representado no **tarefas** janela como ela está o **Threads** janela, por um azul *pausar* ícone.  
  
## <a name="summary"></a>Resumo  
 Este passo a passo demonstrou o **tarefas paralelas** e **pilhas paralelas** janelas do depurador. Use essas janelas em projetos reais que utilizam código multi-threaded. Você pode examinar o código paralelo escrito no C++, no C# ou no Visual Basic.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos multithread](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Programação paralela](/dotnet/standard/parallel-programming/index)   
 [Tempo de execução de simultaneidade](/cpp/parallel/concrt/concurrency-runtime)   
 [Usando a janela pilhas paralelas](../debugger/using-the-parallel-stacks-window.md)   
 [Usando a janela Tarefas](../debugger/using-the-tasks-window.md)