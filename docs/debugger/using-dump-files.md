---
title: Usar arquivos de despejo | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 03/08/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b06f88433f8b744a9bea7dfcce95b0a095cf7890
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481821"
---
# <a name="use-dump-files-with-visual-studio"></a>Usar arquivos de despejo com o Visual Studio
Arquivos de despejo com ou sem heaps; criar um arquivo de despejo de memória. abrir um arquivo de despejo de memória; Localize os binários, o do pdb e o arquivo de origem para um arquivo de despejo.
  
##  <a name="BKMK_What_is_a_dump_file_"></a> O que é um arquivo de despejo?  
 Um *arquivo de despejo* é um instantâneo de um aplicativo no ponto no tempo de despejo de memória é necessário. Ele mostra que processo estava sendo executado e que módulos foram carregados. Se o despejo foi salvo com informações de heap, o arquivo de despejo conterá um instantâneo do que estava na memória do aplicativo naquele momento. Abrir um arquivo de despejo com um heap no Visual Studio é como parar em um ponto de interrupção em uma sessão de depuração. Embora não seja possível continuar a execução, você pode examinar as pilhas, os threads e os valores das variáveis do aplicativo no momento em que o despejo ocorreu.  
  
 Despejos de memória são usados principalmente para depurar problemas que ocorrem nas máquinas que o desenvolvedor não tem acesso. Por exemplo, você pode usar um arquivo de despejo de memória da máquina do cliente quando você não pode reproduzir a falha do cliente ou de suspensão no seu computador. Os despejos também são criados por testadores para salvar dados de pane ou parada para que o computador de teste possa ser usado para mais testes. O depurador do Visual Studio pode salvar arquivos de despejo para código gerenciado ou nativo. O depurador pode carregar arquivos de despejo criados pelo Visual Studio ou por outros programas que salvem arquivos de *minidespejo* formato.  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Arquivos de despejo, com ou sem heaps  
 Você pode criar arquivos de despejo com ou sem informações de heap.  
  
-   **Despejar arquivos com heaps** contêm um instantâneo de memória do aplicativo. Isso inclui os valores das variáveis no momento em que o despejo foi criado. Se você carregar um arquivo de despejo que foi salvo com um heap, o Visual Studio poderá carregar os símbolos, mesmo se o binário do aplicativo não for encontrado. O Visual Studio também salva os binários de módulos nativos carregados no arquivo de despejo, o que pode facilitar muito a depuração.  
  
-   **Despejar arquivos sem heaps** são bem menores do que os despejos de memória com as informações de heap. No entanto, o depurador precisa carregar os binários de aplicativo para localizar as informações do símbolo. Os binários devem ter uma correspondência exata dos binários que foram usados quando o despejo foi criado. Somente os valores das variáveis de pilha são salvos em arquivos de despejo sem dados de heap.  
  
##  <a name="BKMK_Requirements_and_limitations"></a> Requisitos e limitações  
  
-   Depurar arquivos de despejo de código otimizado pode ser confuso. Por exemplo, o compilador com funções embutidas pode resultar em pilhas de chamadas inesperadas e outras otimizações podem alterar o tempo de vida de variáveis.  
  
-   Os arquivos de despejo de computadores de 64 bits devem ser depurados em uma instância do Visual Studio em execução em um computador de 64 bits.  
  
-   Em versões do Visual Studio anteriores ao VS 2013, os despejos de aplicativos de 32 bits que eram executados em computadores de 64 bits que foram coletados por algumas ferramentas (como o Gerenciador de Tarefas e o WinDbg de 64 bits) não podiam ser abertos no Visual Studio. Essa limitação foi removida do VS 2013.  
  
-   O Visual Studio pode depurar arquivos de despejo de aplicativos nativos em dispositivos ARM. O Visual Studio também pode depurar arquivos de despejo de aplicativos gerenciados em dispositivos ARM, mas somente no depurador nativo.  
  
-   Para depurar [modo kernel](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) arquivos de despejo, baixe as ferramentas de depuração para Windows que faz parte do [Windows Driver Kit (WDK)](/windows/hardware/windows-driver-kit). 
  
-   O Visual Studio não pode depurar arquivos de despejo salvos no formato de despejo mais antigo, conhecido como um [despejo do modo de usuário completo](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx). Observe que um despejo completo do modo de usuário não é igual a um despejo com heap.  
  
-   Para depurar com o [SOS.dll (extensão de depuração SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension) no Visual Studio, você deve instalar as ferramentas de depuração para Windows que faz parte do [Windows Driver Kit (WDK)](/windows/hardware/windows-driver-kit) 
  
##  <a name="BKMK_Create_a_dump_file"></a> Criar um arquivo de despejo  
 Para criar um arquivo de despejo com o Visual Studio:  
  
-   Enquanto você estiver depurando um processo no Visual Studio, será possível salvar um arquivo de despejo quando o depurador parar em uma exceção ou em um ponto de interrupção. Escolha **depurar**, em seguida, **Salvar despejo como**, em seguida, **depurar**. No **Salvar despejo como** na caixa de **Salvar como tipo** lista, você pode selecionar **minidespejo** ou **minidespejo com Heap** (o padrão).  
  
-   Com [depuração Just-in-](../debugger/just-in-time-debugging-in-visual-studio.md) habilitado, você pode anexar o depurador a um processo falhado está em execução fora do depurador e, em seguida, salve um arquivo de despejo. Consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 Você também pode criar arquivos de despejo com qualquer programa que ofereça suporte ao formato de minidespejo do Windows. Por exemplo, o **Procdump** utilitário de linha de comando do [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) pode criar arquivos de despejo de falha do processo com base em gatilhos ou sob demanda. Consulte [requisitos e limitações](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) neste tópico para obter informações adicionais sobre como usar outras ferramentas para criar arquivos de despejo. 
  
##  <a name="BKMK_Open_a_dump_file"></a> Abrir um arquivo de despejo  
  
1.  No Visual Studio, escolha **arquivo**, **abrir**, **arquivo**.  
  
2.  No **abrir arquivo** caixa de diálogo caixa, localize e selecione o arquivo de despejo. Geralmente, ele terá uma extensão .dmp. Em seguida, escolha **Okey**.  
  
3.  O **resumo do arquivo de despejo** janela é exibida. Nessa janela, você pode exibir informações resumidas da depuração do arquivo de despejo, definir o caminho do símbolo, iniciar a depuração e copiar as informações resumidas na área de transferência.  
  
     ![Página de resumo de minidespejo](../debugger/media/dbg_dump_summarypage.png "DBG_DUMP_SummaryPage")  
  
4.  Para iniciar a depuração, vá para o **ações** seção e escolha a opção **depurar com somente gerenciado**, **depurar com somente nativo** ou **depurar com Mixed**.  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Localizar os binários, arquivos de símbolo (. PDB) e arquivos de origem  
 Para usar os recursos completos do Visual Studio a fim de depurar um arquivo de despejo, você precisar acessar:  
  
-   O arquivo .exe para o qual o despejo foi feito e outros binários (DLL, etc.) que foram usados no processo de despejo.  
  
     Se você estiver depurando um despejo com dados de heap, o Visual Studio poderá lidar com binários ausentes para alguns módulos, mas deverá ter binários para módulos suficientes de modo a gerar pilhas de chamadas válidas. O Visual Studio inclui os módulos nativos em um arquivo de despejo com heap.  
  
-   Arquivos de símbolo (.pdb) para o .exe e outros binários.  
  
-   Arquivos de origem para os módulos em que você está interessado.  
  
     Os arquivos executável e .pdb devem corresponder exatamente à versão e à compilação dos arquivos usados quando o despejo foi criado.  
  
     Você pode depurar usando a desmontagem dos módulos, se você não encontrar os arquivos de origem  
  
 **Caminhos de pesquisa padrão para arquivos executáveis**  
  
 O Visual Studio procura automaticamente esses locais de arquivos executáveis que não estão incluídos no arquivo de despejo:  
  
1.  O diretório que contém o arquivo de despejo.  
  
2.  O caminho do módulo que é especificado no arquivo de despejo. Esse é o caminho do módulo no computador onde o despejo foi coletado.  
  
3.  Os caminhos de símbolo especificados no **depuração**, **opções**, **símbolos** página do Visual Studio **ferramentas**, **opções**  caixa de diálogo. Você pode adicionar mais locais para pesquisa nessa página.  
  
 **Usando o binário não > Símbolo > páginas de origem**  
  
 Se o Visual Studio não pode localizar os arquivos necessários para um módulo no despejo de depuração, ele exibe uma página apropriada (**nenhum binário encontrado**, **sem símbolos encontrados**, ou **nenhuma fonte encontrada**). Essas páginas fornecem informações detalhadas sobre a causa do problema e fornecem links de ação que podem ajudar a identificar o local correto dos arquivos. Consulte [especificar símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depuração Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Especifique o símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)