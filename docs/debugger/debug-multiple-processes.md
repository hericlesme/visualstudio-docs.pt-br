---
title: "Depurar vários processos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0696a9e45727c5d62f275d0574d5ec54e378038
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debug-multiple-processes"></a>Vários processos de depuração
Aqui está como iniciar a depuração de processos, alternar entre processos, interromper e continuar a execução, percorrer o código-fonte, pare a depuração e encerrar ou desanexar de processos.  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Configurar o comportamento de vários processos em execução  
 Por padrão, quando vários processos são executados no depurador, os comandos de quebra, avanço e interrupção do depurador geralmente afetam todos os processos. Por exemplo, quando um processo é suspenso em um ponto de interrupção, a execução de todos outros processos é suspendida também. Você pode alterar esse comportamento padrão para obter mais controle sobre os destinos dos comandos de execução.  
  
1.  Clique em **Depurar > Opções e configurações**.  
  
2.  Sobre o **depuração**, **geral** página, desmarque o **interromper todos os processos quando um processo for interrompido** caixa de seleção.  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Localizar a origem e o símbolo de arquivos (. PDB)  
 Para navegar no código-fonte de um processo, o depurador precisa acessar os arquivos de origem e os arquivos do símbolo do processo. Consulte [especificar símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Se você não pode acessar os arquivos para um processo, você pode navegar usando a janela de desmontagem. Consulte [como: usar a janela de desmontagem](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Iniciar vários processos em uma solução do VS, anexar a um processo, iniciar automaticamente um processo no depurador  
  
-   [Iniciar a depuração de vários processos em uma solução do Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution)  
  
-   [Alterar o projeto de inicialização](#BKMK_Change_the_startup_project)  
  
-   [Iniciar um projeto específico em uma solução](#BKMK_Start_a_specific_project_in_a_solution)  
  
-   [Iniciar vários projetos em uma solução](#BKMK_Start_multiple_projects_in_a_solution)  
  
-   [Anexar a um processo](#BKMK_Attach_to_a_process)  
  
-   [Iniciar automaticamente um processo no depurador](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  O depurador não é anexado automaticamente a um processo filho que é inicializado por um processo depurado, mesmo se o projeto filho estiver na mesma solução. Para depurar um processo filho:  
>   
>  -   Anexar ao processo filho depois que for iniciado.  
>   
>      -ou-  
> -   Configurar o Windows para iniciar automaticamente o processo filho em uma nova instância do depurador.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Iniciar a depuração de vários processos em uma solução do Visual Studio  
 Quando você tiver mais de um projeto em uma solução do Visual Studio que pode executar de forma independente (projetos que são executados em processos separados), será possível selecionar quais projetos o depurador inicia.  
  
 ![Alterar o tipo de inicialização para um projeto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a>Alterar o projeto de inicialização  
 Para alterar o projeto de inicialização para uma solução, selecione o projeto no Gerenciador de soluções e escolha **definir como projeto de inicialização** no menu de contexto.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a>Iniciar um projeto específico em uma solução  
 Para iniciar um projeto para uma solução sem alterar o projeto de inicialização padrão, selecione o projeto no Gerenciador de soluções e escolha **depurar** no menu de contexto. Você pode escolher **iniciar nova instância** ou **intervir nova instância**.  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [iniciar vários processos em uma solução do VS, anexar a um processo, iniciar automaticamente um processo no depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a>Iniciar vários projetos em uma solução  
  
1.  Selecione a solução no Gerenciador de soluções e escolha **propriedades** no menu de contexto.  
  
2.  Selecione **propriedades comuns**, **projeto de inicialização** no **propriedades** caixa de diálogo.  
  
3.  Para cada projeto que você deseja alterar, escolha **iniciar**, **iniciar sem depuração**, ou **nenhum**.  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [iniciar vários processos em uma solução do VS, anexar a um processo, iniciar automaticamente um processo no depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a>Anexar a um processo  
 O depurador pode também a *anexar* para programas que são executados em processos fora do Visual Studio, incluindo programas em execução em um dispositivo remoto. Após vincular-se a um programa, você poderá usar comandos de execução do depurador, inspecionar o estado do programa e assim por diante. A capacidade de inspecionar o programa pode ser limitada se o programa foi criado com informações de depuração, se você tem acesso ao código-fonte do programa, e se o compilador just-in-time (JIT) do Common Language Runtime está controlando as informações de depuração.  
  
 Consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) para obter mais informações.  
  
 **Anexar a um processo que está em execução no computador local**  
  
 Clique em **Depurar > Anexar ao processo**. Sobre o **anexar ao processo** caixa de diálogo, selecione o processo do **processos disponíveis** lista e, em seguida, escolha **anexar**.  
  
 ![Anexar a caixa de diálogo processo](../debugger/media/dbg_attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Iniciar automaticamente um processo no depurador  
 Às vezes, pode ser necessário depurar o código de inicialização para um programa que foi iniciado por outro processo. Os exemplos incluem serviços e ações de configuração personalizada. Nesses cenários, você poderá fazer com que o depurador seja iniciado e automaticamente anexado quando seu aplicativo iniciar.  
  
1.  Iniciar o Editor do registro (**regedit.exe**).  
  
2.  Navegue até o **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** pasta.  
  
3.  Selecione a pasta do aplicativo que você deseja iniciar o depurador.  
  
     Se o nome do aplicativo não estiver listado como uma pasta filho, selecione **opções de execução do arquivo de imagem** e, em seguida, escolha **novo**, **chave** no menu de contexto. Selecione a nova chave, escolha **Renomear** no menu de atalho e, em seguida, digite o nome do aplicativo.  
  
4.  No menu de contexto da pasta de aplicativo, escolha **novo**, **valor de cadeia de caracteres**.  
  
5.  Alterar o nome do novo valor de **novo valor** para `debugger`.  
  
6.  No menu de contexto da entrada do depurador, escolha **modificar**.  
  
7.  Na caixa de diálogo Editar cadeia de caracteres, digite `vsjitdebugger.exe` no **dados do valor** caixa.  
  
     ![Editar caixa de diálogo de cadeia de caracteres](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
 ![Depurador automática iniciar entrada em regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "DBG_Execution_AutomaticStart_Result")  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Alternar processos, interromper e continuar a execução, percorrer o código-fonte  
  
-   [Alternar entre processos](#BKMK_Switch_between_processes)  
  
-   [Quebrar, etapa e continue comandos](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a>Alternar entre processos  
 Você pode conectar-se a vários processos quando está depurando, mas somente um processo está ativo no depurador em um determinado momento. Você pode definir ativo ou *atual* processo na barra de ferramentas Depurar local ou no **processos** janela. Para alternar entre processos, ambos os processos devem estar no modo de interrupção.  
  
 **Para definir o processo atual**  
  
-   Na barra de ferramentas Depurar local, escolha **processo** para exibir o **processo** caixa de listagem. Selecione o processo que você deseja designar como o processo atual.  
  
     ![Alternar entre processos](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
     Se o **local do depurador** barra de ferramentas não estiver visível, escolha **ferramentas**, **personalizar**. Sobre o **barras de ferramentas** guia, escolha **local do depurador**.  
  
-   Abra o **processos** janela (atalho **Ctrl + Alt + Z**), localize o processo que você deseja definir como o processo atual e clique duas vezes nele.  
  
     ![Janela de processos](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")  
  
     O processo atual é marcado por uma seta amarela.  
  
 Alternar para um projeto o torna o processo atual para fins de depuração. Qualquer janela do depurador que você exibir mostrará o estado do processo atual e todos os comandos das etapas afetarão somente o processo atual.  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [alternar processos, interromper e continuar a execução, percorrer o código-fonte](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a>Quebrar, etapa e continue comandos  
  
> [!NOTE]
>  Por padrão, os comandos interromper, continuar e avançar depurador afetam todos os processos que estão sendo depurados. Para alterar esse comportamento, consulte [configurar o comportamento de vários processos em execução](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Comando**|**Interromper todos os processos quando um processo for interrompido**<br /><br /> Verificado (Padrão)|**Interromper todos os processos quando um processo for interrompido**<br /><br /> Limpo|  
|**Depurar** menu:<br /><br /> -   **Interromper tudo**|Todos os processos são interrompidos.|Todos os processos são interrompidos.|  
|**Depurar** menu:<br /><br /> -   **Continuar**|Todos os processos são retomados.|Todos os processos suspensos são retomados.|  
|**Depurar** menu:<br /><br /> -   **Intervir**<br />-   **Depuração parcial**<br />-   **Sair**|Todos os processos estão em execução durante as etapas de processo atual.<br /><br /> Em seguida, todos os processos são interrompidos.|Etapas de processo atual.<br /><br /> Retomada de processos suspensos.<br /><br /> Executando a continuação dos processos.|  
|**Depurar** menu:<br /><br /> -   **Etapa no processo atual**<br />-   **Etapa do processo atual**<br />-   **Sair do processo atual**|N/D|Etapas de processo atual.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|Janela de origem<br /><br /> -   **Ponto de interrupção**|Todos os processos são interrompidos.|Somente quebras do processo da janela de origem.|  
|Menu de contexto da janela de origem:<br /><br /> -   **Executar até o cursor**<br /><br /> A janela de origem deve estar no processo atual.|Todos os processos estão em execução enquanto o processo da janela de origem executa ao cursor e depois interrompe.<br /><br /> Em seguida, todos os outros processos não interrompidos.|O processo da janela de origem é executado para o cursor.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|**Processos** menu de contexto da janela:<br /><br /> -   **Interromper o processo**|N/D|Quebras selecionadas do processo.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|**Processos** menu de contexto da janela:<br /><br /> -   **Continuar o processo**|N/D|O processo selecionado é retomado.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [alternar processos, interromper e continuar a execução, percorrer o código-fonte](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Parar a depuração, encerrar ou desanexar de processos  
  
-   [Parar, encerrar e desanexar comandos](#BKMK_Stop__terminate__and_detach_commands)  
  
 Por padrão, quando você escolhe **depurar**, **parar depuração** quando vários processos estão abertos no depurador, o depurador termina ou se desconecta de todos os processos, dependendo de como o processo foi aberto do depurador:  
  
-   Se o processo atual foi iniciado no depurador, esse processo é finalizado.  
  
-   Se você já anexou o depurador ao processo atual, o depurador será desanexado do processo e o deixará em execução.  
  
 Por exemplo, se você iniciar a depuração de um processo em uma solução do Visual Studio, anexe a outro processo já está em execução e, em seguida, escolha **parar depuração**, a sessão de depuração termina, o processo foi iniciado no Visual Studio é finalizado, enquanto o processo que você está conectado é deixado em execução. Você pode usar os seguintes procedimentos para controlar a maneira que você interrompe a depuração.  
  
> [!NOTE]
>  O **interromper todos os processos quando um processo for interrompido** opção não afeta a parar a depuração ou encerrando e desanexação de processos.  
  
 **Para alterar como parar depuração afeta um processo individual**  
  
-   Abra o **processos** janela (atalho **Ctrl + Alt + Z**). Selecione um processo e, em seguida, marque ou desmarque o **desanexar quando a depuração para** caixa de seleção.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a>Parar, encerrar e desanexar comandos  
  
|||  
|-|-|  
|**Comando**|**Descrição**|  
|**Depurar** menu:<br /><br /> -   **Parar a depuração**|A menos que o comportamento é alterado por **processos** janela **desanexar quando a depuração será interrompido** opção:<br /><br /> 1.  Processos iniciados pelo depurador terminaram.<br />2.  Os processos anexados são separados do depurador.|  
|**Depurar** menu:<br /><br /> -   **Encerrar todas as**|Todos os processos são encerrados.|  
|**Depurar** menu:<br /><br /> -   **Desanexar tudo**|O depurador desanexa todos os processos.|  
|**Processos** menu de contexto da janela:<br /><br /> -   **Desanexar processo**|O depurador dispara do processo selecionado.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|**Processos** menu de contexto da janela:<br /><br /> -   **Encerrar processo**|O processo selecionado é finalizado.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|**Processos** menu de contexto da janela:<br /><br /> -   **Desconectar quando a depuração será interrompido**|Ativa/desativa o comportamento de **depurar**, **parar depuração** do processo selecionado:<br /><br /> -Verificado: O depurador desconecta do processo.<br />-Desmarcada: O processo foi finalizado.|  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [parar a depuração, encerrar ou desanexar de processos](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Voltar ao início](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Conteúdo](#BKMK_Contents)  
  
## <a name="see-also"></a>Consulte também  
 [Especifique o símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navegar pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Depuração Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)