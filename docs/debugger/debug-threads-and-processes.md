---
title: Ferramentas para depurar threads e processos | Microsoft Docs
ms.custom: ''
ms.date: 04/21/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f42159b15bbba4bd092dcde34404459212e26ab3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477362"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Ferramentas para depurar threads e processos no Visual Studio
*Threads* e *processos* são conceitos relacionados em ciência da computação. Ambos representam sequências de instruções que devem executar em uma ordem específica. Instruções em threads ou processos separados, entretanto, podem ser executados em paralelo.  
  
 Os processos existem no sistema operacional e correspondem ao que os usuários veem como programas ou aplicativos. Um thread, por outro lado, existe dentro de um processo. Por esse motivo, threads são, às vezes, denominados *processos leves*. Cada processo consiste em um ou mais threads.  
  
 A existência de vários processos permite que um computador execute mais de uma tarefa de cada vez. A existência de vários threads permite que um processo separe o trabalho a ser executado paralelamente. Em um computador com multiprocessadores, os processos ou threads podem ser executados em processadores diferentes. Isso permite o verdadeiro processamento paralelo.  
  
 O processamento paralelo perfeito não é sempre possível. Às vezes os threads devem ser sincronizados. Um thread pode ter que aguardar um resultado de outro thread, ou um thread pode precisar de acesso exclusivo a um recurso que outro thread está usando. Problemas de sincronização são uma causa comum de erro em aplicativos com multithreads. Em alguns casos, os threads podem interromper espera de um recurso que nunca fica disponível. Isso resulta em uma condição chamada *deadlock*.  
  
 O depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece ferramentas avançadas e mas fáceis de usar para depurar threads e processos.  
  
## <a name="tools-and-features"></a>Ferramentas e recursos
As ferramentas necessárias para usar em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dependem de qual tipo de código que você está tentando depurar:

- Para processos, são as principais ferramentas de **anexar ao processo** caixa de diálogo, o **processos** janela e o **local do depurador** barra de ferramentas.

- Para threads, são as principais ferramentas para threads de depuração a **Threads** janela, marcadores de thread no windows de origem, **pilhas paralelas** janela, **inspeção paralela** janela, e o **local do depurador** barra de ferramentas.  
  
- Para o código que usa o <xref:System.Threading.Tasks.Task> no [tarefa TPL (biblioteca paralela)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), o [tempo de execução de simultaneidade](/cpp/parallel/concrt/concurrency-runtime/) (código nativo), as principais ferramentas para depurar aplicativos multithread são o **Pilhas paralelas** janela, o **inspeção paralela** janela e o **tarefas** janela (a **tarefas** janela também oferece suporte a Objeto de promessa JavaScript).

- Para threads de depuração na GPU, a principal ferramenta é o **Threads de GPU** windows.  
  
 A tabela a seguir mostra as informações disponíveis e as ações que você pode executar em cada um desses locais:  
  
|Interface do Usuário|Informação disponível|Ações que você pode executar|  
|--------------------|---------------------------|-----------------------------|  
|**Anexar ao processo** caixa de diálogo|Processos disponíveis você pode anexar:<br /><br /> -Nome do processo (.exe)<br />-Número de ID processo<br />-Título barra de menus<br />-Type (gerenciado na v 4.0; V 2.0 gerenciado, v 1.1, v 1.0; x86; x64; IA64)<br />-O nome de usuário (nome de conta)<br />-Número sessão|Selecione um processo anexar.<br /><br /> Selecione um computador remoto<br /><br /> Altere o tipo de transporte para se conectar a computadores remotos|  
|**Processos** janela|Processos anexados:<br /><br /> -Nome do processo<br />-Número de ID processo<br />-Path para processar .exe<br />-Título barra de menus<br />-Estado (quebra. em execução)<br />-Depuração (nativo, gerenciados e assim por diante).<br />-(Padrão, nativo sem autenticação) do tipo de transporte<br />-Qualificador de transporte (computador remoto)|Ferramentas:<br /><br /> -Anexar<br />-Desanexar<br />-Encerrar<br /><br /> O menu de atalho:<br /><br /> -Anexar<br />-Desanexar<br />-Quando a depuração para desanexar<br />-Encerrar|  
|**Threads** janela|Threads durante o processo atual:<br /><br /> -ID do thread<br />-ID gerenciado<br />-Categoria (thread principal, o thread de interface, manipulador de chamada de procedimento remoto ou thread de trabalho)<br />-Nome do thread<br />-O local em que o thread é criado<br />-Prioridade<br />-Máscara de afinidade<br />-Contagem suspensa<br />-Nome do processo<br />-O sinalizador indicador<br />-Indicador suspenso|Ferramentas:<br /><br /> -Pesquisa<br />-Pilha de chamadas pesquisa<br />-Sinalizar apenas meu código<br />-O sinalizador seleção de módulo personalizada<br />-Agrupar por<br />-Colunas<br />-Pilhas de expandir/recolher<br />-Expandir/recolher grupos<br />-Congelar/descongelar Threads<br /><br /> O menu de atalho:<br /><br /> -Mostrar threads na fonte<br />-Alternar para um thread<br />-Congelar um segmento em execução<br />-Descongelar um thread congelado<br />-Sinalizador um thread para estudar detalhes adicionais<br />-Sinalizar um thread<br />-Renomeie um thread<br />-Mostrar e ocultar threads<br /><br /> Outras ações:<br /><br /> -Exibir a pilha de chamadas para um thread em um DataTip|  
|Janela de origem|Indicadores de thread na medianiz esquerda indicam único ou vários threads (desativado por padrão, ativado usando o menu de atalho no **Threads** janela)|O menu de atalho:<br /><br /> -Alternar para um thread<br />-Sinalizador um thread para estudar detalhes adicionais<br />-Sinalizar um thread|  
|**Local de depuração** barra de ferramentas|-Processo atual<br />-Suspender o aplicativo<br />-Reiniciar o aplicativo<br />-Suspender e desligar o aplicativo<br />-Thread atual<br />-Alternar o estado de sinalizador do thread atual<br />-Mostrar somente threads sinalizados<br />-Mostrar somente o processo atual<br />-Quadro de pilhas atual|-Alternar para outro processo<br />-Suspender, continuar ou desligar o aplicativo<br />-Alternar para outro thread no processo atual<br />-Alternar para outro quadro de pilha no thread atual<br />-Sinalizador ou sinalizar threads atuais<br />-Mostrar somente threads sinalizados<br />-Mostrar somente o processo atual|  
|**Paralelo pilhas** janela|-Pilhas de chamadas para vários threads em uma janela.<br />-Quadro de pilha ativa para cada thread.<br />-Chamadores e chamados para qualquer método.|-Filtrar threads especificados<br />-Alternar para modo de exibição tarefas<br />-Sinalizador ou sinalizar um thread<br />-Zoom|   
|**Paralelo inspecionar** janela|-A coluna de sinalizador, no qual você pode marcar um thread que você deseja preste atenção especial.<br />-A coluna quadro no qual uma seta indica que o quadro selecionado.<br />-A coluna configurável que pode exibir a máquina, de processo, peça, tarefa e thread.|-Sinalizador ou sinalizar um thread<br />-Exibe somente threads sinalizados<br />-Quadros chave<br />-Classificar uma coluna<br />-Threads grupo<br />-Congelar ou descongelar threads<br />-Exportar os dados na janela Inspeção paralela| 
|**Tarefas** janela|-Exibir informações sobre <xref:System.Threading.Tasks.Task> objetos, incluindo a ID da tarefa, status da tarefa (agendado, o deadlock em execução, aguardando,) e o segmento que é atribuído à tarefa.<br />-Local atual na pilha de chamadas.<br />-Delegate é passado para a tarefa no momento da criação|-Alternar para a tarefa atual<br />-Sinalizador ou sinalizar uma tarefa<br />-Congelar ou descongelar uma tarefa|  
|**Threads de GPU** janela|-A coluna de sinalizador, no qual você pode marcar um thread que você deseja preste atenção especial.<br />-A coluna de segmento atual, no qual uma seta amarela indica que o thread atual.<br />-A **a contagem de threads** coluna, que exibe o número de threads no mesmo local.<br />-A **linha** coluna, que exibe a linha de código em que cada grupo de threads está localizado.<br />-A **endereço** coluna, que exibe o endereço de instrução em que cada grupo de threads está localizado.<br />-A **local** coluna, que é o local no código do endereço.<br />-A **Status** coluna, que mostra se o thread está ativo ou bloqueado.<br />-A **bloco** coluna, que mostra o índice de bloco para os threads na linha.|-Alteração a um thread diferente<br />-Exibir um bloco específico e o thread<br />-Exibir ou ocultar uma coluna<br />-Classificar por uma coluna<br />-Threads grupo<br />-Congelar ou descongelar threads<br />-Sinalizador ou sinalizar um thread<br />-Exibe somente threads sinalizados|  
  
## <a name="see-also"></a>Consulte também  
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depurando código de GPU](../debugger/debugging-gpu-code.md)