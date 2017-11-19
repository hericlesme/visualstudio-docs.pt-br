---
title: "Navegar pelo código com o depurador do Visual Studio | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cda62de6fe72598674b90e4a0ef5dccd8cf2a2af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="navigate-code-with-the-visual-studio-debugger"></a>Navegar pelo código com o depurador do Visual Studio
Familiarize-se com os comandos e atalhos para navegar pelo código no depurador e que tornará mais rápida e fácil de localizar e resolver problemas em seu aplicativo. Enquanto você navegar pelo código no depurador, você pode inspecionar o estado do seu aplicativo ou saber mais sobre o seu fluxo de execução.  
  
## <a name="start-debugging"></a>Iniciar a depuração  
 Geralmente, você inicia uma sessão de depuração usando **F5** (**depurar** > **iniciar depuração**). Esse comando inicia o aplicativo com o depurador anexado.  
  
 A seta verde também inicia o depurador (mesmo que **F5**).  
  
 ![DBG &#95; Noções básicas sobre &#95; Iniciar &#95; depuração](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
 Outras maneiras que você pode iniciar o aplicativo com o depurador anexado incluem **F11** ([intervir código](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([passar sobre código](#BKMK_Step_over_Step_out)), ou usando **executar até o Cursor**.  Consulte as outras seções neste tópico para obter informações sobre o que fazem essas opções.  
  
 Quando você depura, a linha amarela mostra o código que executará a seguir.  
  
 ![DBG &#95; Noções básicas sobre &#95; Quebra &#95; Modo](../debugger/media/dbg_basics_break_mode.png "DBG_Basics_Break_Mode")  
  
 Durante a depuração, você pode alternar entre os comandos **F5**, **F11** e usar outros recursos descritos neste tópico (como pontos de interrupção) para obter o código que você deseja examinar rapidamente.  
  
 A maioria dos recursos do depurador, como a exibição de valores de variáveis na janela locais ou avaliar expressões na janela Inspeção, estão disponíveis apenas enquanto o depurador está em pausa (também chamado de *modo de interrupção*). Quando o depurador é pausado, o estado do aplicativo está suspenso durante a funções, variáveis, e os objetos permanecem na memória. No modo de interrupção, você pode examinar as posições dos elementos e estados para procurar por violações ou erros. Para alguns tipos de projeto, você também pode fazer ajustes para o aplicativo no modo de interrupção. Para assistir um vídeo mostrando esses recursos, consulte [guia de Introdução com o depurador](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Entrar no código, linha por linha  
 Para interromper em cada linha de código (cada instrução) durante a depuração, use o **F11** atalho de teclado (ou **depurar** > **intervir** no menu).  
  
> [!TIP]
>  Ao executar cada linha de código, você pode focalizar variáveis para ver seus valores, ou use o [locais](../debugger/autos-and-locals-windows.md) e [inspecionar](../debugger/autos-and-locals-windows.md) windows para assistir a alterar seus valores.  
  
 Aqui estão alguns detalhes sobre o comportamento do **intervir**:  
  
-   Em uma chamada de função aninhada, **intervir** etapas em mais profundamente aninhadas função. Se você usar **intervir** em uma chamada como `Func1(Func2())`, o depurador vai para a função `Func2`.  
  
-   O depurador avança realmente com as instruções de código em vez de linhas físicas. Por exemplo, uma cláusula `if` pode ser gravada em uma linha:  
  
    ```CSharp  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```VB  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Quando você entra nessa linha, o depurador trata a condição como uma etapa e a consequência como outra (nesse exemplo, a condição é verdadeira.)  
  
 Para rastrear visualmente a pilha de chamadas durante a depuração em funções, consulte [mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a>Percorrer o código, ignorando a funções  
 Ao executar o código no depurador, geralmente você vai perceber que você não precisa ver o que acontece em uma função específica (não se preocupa- ou se você souber que ele funciona, como o código de biblioteca bem testada). Usar esses comandos para saltar entre código (as funções ainda forem executados, obviamente, mas o depurador ignora-los).  
  
|Comando de teclado|Menu Comando|Descrição|  
|----------------------|------------------|-----------------|  
|**F10**|**Depuração parcial**|Se a linha atual contiver uma chamada de função **contornar** executa o código, em seguida, suspende a execução na primeira linha de código após a função chamada retorna.|  
|**SHIFT + F11.**|**Sair**|**Sair** continua a execução do código e suspende a execução quando a função atual retorna (ignora depurador por meio da função atual).|  
  
> [!TIP]
>  Se você precisa localizar o ponto de entrada em seu aplicativo, inicie com **F10** ou **F11**. Esses comandos geralmente são úteis quando você estiver verificando o estado do aplicativo ou ao tentar encontrar mais informações sobre seu fluxo de execução.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Executar até um local específico ou uma função  
 Geralmente o método preferencial de depuração de código, esses métodos são úteis quando você sabe exatamente o código que deseja inspecionar ou, pelo menos você souber onde você deseja iniciar a depuração.  
  
-   **Defina pontos de interrupção no código**  
  
     Para definir um ponto de interrupção simples em seu código, abra o arquivo de origem no editor do Visual Studio. Defina o cursor na linha de código em que você deseja suspender a execução e, em seguida, clique na janela de código para ver o menu de contexto e escolha **ponto de interrupção > Inserir ponto de interrupção** (ou pressione **F9**). O depurador suspende o direito de execução antes que a linha seja executada.  
  
     ![Definir um ponto de interrupção](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Os pontos de interrupção no Visual Studio fornecem um conjunto rico de funcionalidades adicionais, como pontos de interrupção e pontos de monitoramento condicionais. Consulte [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
-   **Executar até o local do cursor**  
  
     Para executar a localização do cursos, coloque o cursor em uma linha executável do código em uma janela de origem. No menu de contexto do editor (com o botão direito no editor), escolha **executar até o Cursor**. Isso é como configurar um ponto de interrupção temporário.

-   **Execute a clique** 

    Para executar a um ponto no seu código enquanto está em pausa no depurador, selecione o **execução aqui** ícone de seta verde (você verá o ícone ao passar o mouse sobre uma linha de código). Isso elimina a necessidade de definir pontos de interrupção temporários.

    ![Depurador do executado para clique](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

    > [!NOTE]
    > **Execute a clique** é novo no [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].
  
-   **Quebrar manualmente em código**  
  
     Para interromper a próxima linha de código em um aplicativo em execução disponível, escolha **depurar**, **quebra todos** (teclado: **Ctrl + Alt + Break**). 
  
     Se você interromper a execução de código sem a fonte correspondente ou símbolo (. PDB) arquivos), o depurador exibirá uma **arquivos de origem não encontrado** ou um **símbolos não encontrados** página que pode ajudá-lo a encontrar apropriada arquivos. Consulte [especificar símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Se não for possível acessar os arquivos de suporte, você ainda poderá depurar as instruções de assembly na janela de desmontagem.  
  
-   **Executar uma função na pilha de chamadas**  
  
     No **pilha de chamadas** janela (disponível durante a depuração), selecione a função, clique com botão direito e escolha **executar até o Cursor**. Para rastrear visualmente a pilha de chamadas, consulte [mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Executar uma função especificada por nome**  
  
     Você pode fazer o depurador para executar o aplicativo até alcançar uma função especificada. É possível especificar a função por nome ou escolhê-la da pilha de chamadas.  
  
     Para especificar uma função por nome, escolha **depurar**, **novo ponto de interrupção**, **interromper na função**, em seguida, digite o nome da função e outras informações de identificação.  
  
     ![Caixa de diálogo Novo ponto de interrupção](../debugger/media/dbg_execution_newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Se a função está sobrecarregada ou se está no namespace vários, você pode escolher as funções que você deseja o **escolher pontos de interrupção** caixa de diálogo.  
  
     ![Escolha a caixa de diálogo de pontos de interrupção](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a>Mova o ponteiro para alterar o fluxo de execução  
 Enquanto o depurador está pausado, você pode mover o ponteiro de instrução para definir a próxima instrução de código a ser executado. Uma seta amarela na margem de uma fonte ou janela de desmontagem marca o local da próxima instrução a ser executada. Movendo essa seta, você pode ignorar uma parte do código ou retornar a uma linha executada anteriormente. É possível usar esse procedimento para situações como ignorar uma seção de código que contém um bug conhecido.  
  
 ![Mover o ponteiro](../debugger/media/dbg_basics_example3.gif "DBG_Basics_Example3")
  
 Para definir a próxima instrução a executar, use um dos seguintes procedimentos:  
  
-   Em uma janela de origem, arraste a seta amarela para um local onde você deseja definir a instrução seguinte no mesmo arquivo de origem  
  
-   Em uma janela de origem, defina o cursor na linha que você deseja executar em seguida, clique com botão direito e escolha **definir próxima instrução**.  
  
-   Na janela de desmontagem, defina o cursor sobre a instrução de assembly que você deseja executar em seguida, clique em um e escolha **definir próxima instrução**.  
  
> [!CAUTION]
>  Definir a instrução a seguir faz com que o contador do programa pule diretamente para a nova localização. Use este comando com cuidado:  
>   
>  -   As instruções entre os pontos de execução antigos e novos não são executadas.  
> -   Se você mover o ponto de execução para trás, as instruções intervenientes não serão desfeitas.  
> -   Mover a instrução seguinte para outra função ou escopo normalmente resulta em danos à pilha de chamadas, causando um erro em tempo de execução ou uma exceção. Se você tentar mover a instrução seguinte para outro escopo, o depurador abrirá uma caixa de diálogo com um aviso e dará uma chance de cancelar a operação. No Visual Basic, você não pode mover a instrução seguinte para outro escopo ou função.  
> -   No C++ nativo, se você tiver as verificações de tempo de execução ativadas, definir a instrução seguinte poderá fazer com que uma exceção seja gerada quando a execução chegar ao final do método.  
> -   Quando editar e continuar estiver ativado, **definir próxima instrução** falhará se você fez edições que editar e continuam não é possível remapear imediatamente. Isso pode ocorrer, por exemplo, se você editou o código dentro de um bloco catch. Quando isso acontece, você verá uma mensagem de erro que informa que a operação não é suportada.  
  
> [!NOTE]
>  No código gerenciado, você não pode mover a instrução seguinte nas seguintes circunstâncias:  
>   
>  -   A instrução a seguir é um método diferente do que a instrução atual.  
> -   A depuração foi iniciada com a depuração Just-In-Time.  
> -   Um desenrolamento de pilha de chamada está em andamento.  
> -   Uma exceção System.StackOverflowException ou System.Threading.ThreadAbortException foi lançada.  
  
 Não é possível definir a próxima instrução durante a execução ativa do seu aplicativo. Para definir a próxima instrução, o depurador deve estar no modo de interrupção.  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Step-into do código não-usuário  
 Por padrão, o depurador tenta para mostrar apenas o código de aplicativo durante a depuração, que é determinado por um depurador chamada *apenas meu código*. (Consulte [apenas meu código](../debugger/just-my-code.md) para ver como isso funciona para diferentes tipos de projeto e os idiomas e como você pode personalizar o comportamento.) No entanto, às vezes, enquanto você está depurando, convém examinar o código do framework, o código da biblioteca de terceiros ou chamadas para o sistema operacional (chamadas do sistema).  
  
 Você pode desativar apenas meu código acessando **ferramentas** > **opções** > **depuração** e desmarque o **habilitar apenas meu código** caixa de seleção.  
  
 Quando apenas meu código está desabilitado, o depurador pode entrar em código não-usuário e código de usuário não é exibido nas janelas do depurador.  
  
> [!NOTE]
>  Apenas Meu Código não é suportada para projetos de dispositivo.  
  
 **Intervir chamadas do sistema**  
  
 Se você carregar símbolos de depuração de código do sistema e apenas meu código não está habilitado, você pode depurar em uma chamada de sistema como qualquer outra chamada.  
  
 Para acessar arquivos de símbolos da Microsoft, consulte [usar servidores de símbolos para localizar arquivos de símbolo não em sua máquina local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) no [especificar símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) tópico.  
  
 Para carregar símbolos para um componente do sistema específico enquanto você depura:  
  
1.  Abra a janela módulos (teclado: **Ctrl + Alt + U**).  
  
2.  Selecione o módulo para os quais você deseja carregar os símbolos.  
  
     Você pode informar quais módulos têm símbolos carregados examinando o **Status símbolo** coluna.  
  
3.  Escolha **carregar símbolos** no menu de contexto.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Entrar em propriedades e operadores em código gerenciado  
 O depurador considera propriedades e operadores no código gerenciado por padrão. Na maioria dos casos, isso proporciona uma melhor experiência de depuração. Para habilitar a depuração em propriedades ou operadores, escolha **depurar** > **opções**. Sobre o **depuração** > **geral** página, desmarque o **percorrer propriedades e operadores (somente gerenciado)** caixa de seleção