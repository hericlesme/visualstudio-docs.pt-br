---
title: "Anexar a processos em execução com o depurador do Visual Studio | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7ed9c7f362399d9cd256b02af9f1fe1bcecf8ce
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anexar aos processos em execução com o Depurador do Visual Studio
Você pode anexar o depurador do Visual Studio para um processo em execução em um computador local ou remoto. Depois que o processo está sendo executado, clique em **Depurar > Anexar ao processo** (ou pressione **CTRL + ALT + P**) para abrir o **anexar ao processo** caixa de diálogo.

Você pode usar esse recurso para depurar aplicativos em execução em um computador local ou remoto, depurar vários processos simultaneamente ou depurar um aplicativo que não foi criado no Visual Studio. Geralmente é útil quando você deseja depurar um aplicativo, mas (por qualquer motivo) você não iniciou o aplicativo do Visual Studio com o depurador anexado. Por exemplo, se você estiver executando o aplicativo sem o depurador e uma exceção de ocorrências, você pode, em seguida, anexar ao processo que está executando o aplicativo para iniciar a depuração.

> [!TIP]
> Não tem certeza se você precisar usar **anexar ao processo** para seu cenário de depuração? Consulte [comuns de cenários de depuração](#BKMK_Scenarios). Se você deseja depurar aplicativos ASP.NET que foram implantados no IIS, consulte [ASP.NET de depuração remota em um computador remoto do IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a>Anexar a um processo em execução no computador local  
 Para anexar a um processo, você deve saber o nome do processo (consulte [comuns de cenários de depuração](#BKMK_Scenarios) para alguns nomes de processo comum).
  
1.  No Visual Studio, selecione **Depurar > Anexar ao processo** (ou pressione **CTRL + ALT + P**).

    Se você quiser reconectar rapidamente a um processo em vez disso, consulte [anexe ao processo](#BKMK_reattach).
  
2.  No **anexar ao processo** caixa de diálogo caixa, localize o programa que você deseja anexar a partir de **processos disponíveis** lista.  

     Para selecionar rapidamente o processo que você deseja, digite a primeira letra do nome do processo. Se você não souber o nome do processo, consulte [comuns de cenários de depuração](#BKMK_Scenarios).
     
     ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
     Se o processo está sendo executado em uma conta de usuário diferente, selecione o **Mostrar processos de todos os usuários** caixa de seleção.
  
3.  No **anexar a** caixa, certifique-se de que o tipo de código que você irá depurar está listado. O padrão **automáticas** configuração tenta determinar o tipo de código que você deseja depurar. Para definir o tipo de código manualmente, faça o seguinte  
  
    1.  No **anexar a** , clique em **selecione**.  
  
    2.  No **Selecionar tipo de código** caixa de diálogo, clique em **depurar esses tipos de código** e selecione os tipos para depurar.  
  
    3.  Clique em **OK**.  
  
4.  Clique em **Anexar**.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Anexar a um processo em um computador remoto  
 Para anexar a um processo, você deve saber o nome do processo (consulte [comuns de cenários de depuração](#BKMK_Scenarios) para alguns nomes de processo comum). Para obter orientação mais completa para aplicativos ASP.NET que foram implantados no IIS, consulte [ASP.NET de depuração remota em um computador remoto do IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Para outros aplicativos, você poderá localizar o nome do processo no Gerenciador de tarefas.
  
 Quando você usa o **anexar ao processo** caixa de diálogo, você pode selecionar outro computador que foi configurado para depuração remota. Para obter mais informações, consulte [depuração remota](../debugger/remote-debugging.md). Quando você tiver selecionado um computador remoto, poderá exibir uma lista de processos disponíveis que estão em execução no computador e anexá-la a um ou mais processos para depuração.
  
 **Para selecionar um computador remoto:**  

1. No Visual Studio, selecione **Depurar > Anexar ao processo** (ou pressione **CTRL + ALT + P**).

    Se você quiser reconectar rapidamente a um processo em vez disso, consulte [anexe ao processo](#BKMK_reattach).

2.  No **anexar ao processo** caixa de diálogo, selecione tipo de conexão apropriado a **transporte** lista. **Padrão** é a configuração correta para a maioria dos casos.

    O **transporte** configuração persiste entre as sessões de depuração. 
  
3.  Use o **qualificador** caixa de lista para escolher o nome do computador remoto por um dos seguintes métodos:  
  
    1.  Digite o nome no **qualificador** caixa de listagem.
    
        >**Observação** se, em etapas posteriores, você não pode se conectar usando o nome do computador remoto, use o endereço IP. (O número da porta pode aparecer automaticamente depois de selecionar o processo. Você pode também inseri-lo manualmente. Na ilustração abaixo, 4020 é a porta padrão para o depurador remoto.)  

        Se você quiser usar o **localizar** botão, talvez você precise [abra a porta UDP 3702](../debugger/remote-debugger-port-assignments.md) no servidor.
  
    2.  Clique na seta suspensa anexada para o **qualificador** caixa de listagem e selecione o nome do computador na lista suspensa.  
  
    3.  Clique no **localizar** lado a**qualificador** lista para abrir o **Selecionar Conexão de depurador remoto** caixa de diálogo. O **Selecionar Conexão de depurador remoto** caixa de diálogo lista todos os dispositivos que estão em sua sub-rede local e qualquer dispositivo que está diretamente conectado ao computador por um cabo Ethernet. Clique no computador ou dispositivo que você deseja e, em seguida, clique em **selecione**. 
  
     O **qualificador** configuração persiste entre as sessões de depuração somente se uma conexão bem-sucedida de depuração ocorre com esse qualificador.
     
4.  Clique em **atualizar**.

      O **processos disponíveis** lista é exibida automaticamente quando você abre o **processos** caixa de diálogo. Os processos podem iniciar e parar em segundo plano quando a caixa de diálogo está aberta. No entanto, o conteúdo nem sempre será atual. Você pode atualizar a lista a qualquer momento para ver a lista atual de processos clicando **atualizar**. 
     
4.  No **anexar ao processo** caixa de diálogo caixa, localize o programa que você deseja anexar a partir de **processos disponíveis** lista.

     Para selecionar rapidamente o processo que você deseja, digite a primeira letra do nome do processo. Se você não souber o nome do processo, consulte [comuns de cenários de depuração](#BKMK_Scenarios).
  
     Se o processo está sendo executado em uma conta de usuário diferente, selecione o **Mostrar processos de todos os usuários** caixa de seleção.
     
5.  Clique em **Anexar**.

## <a name="BKMK_reattach"></a>Anexe ao processo

Você pode anexar novamente rapidamente para processos que estavam anteriormente conectados a, escolhendo **Depurar > anexe ao processo...** (**Shift + Alt + P**). Quando você escolhe este comando, o depurador imediatamente tentará anexar à última processos anexados usando o **anexar ao processo** caixa de diálogo.

O depurador será reanexar primeiro tentando corresponder à ID do processo anterior e, se isso falhar, correspondendo ao nome do processo anterior. Se nenhuma correspondência for encontrada, ou se houver vários processos encontrados com o mesmo nome, o **anexar ao processo** caixa de diálogo será exibida para que você possa selecionar o processo correto.

> [!NOTE]
> O **anexe ao processo** command é novo no Visual Studio de 2017.

## <a name="additional-info"></a>Informações adicionais

Você pode estar associado a vários programas enquanto depura, mas somente um programa está ativo no depurador em um determinado momento. Você pode definir o programa ativo no **local do depurador** barra de ferramentas ou **processos** janela. Para obter mais informações, consulte [como: definir o programa atual](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
Se você tentar anexar a um processo de propriedade de uma conta de usuário não confiável, aparecerá uma confirmação da caixa de diálogo de aviso de segurança. Para obter mais informações, consulte [aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou se você não tiver certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
Em alguns casos, quando você depurar em uma sessão de área de trabalho remota (serviços de Terminal), o **processos disponíveis** lista não exibirá todos os processos disponíveis. Se você estiver executando o Visual Studio como um usuário que tenha uma conta de usuário limitado a **processos disponíveis** lista não mostrará processos em execução na sessão 0, que é usada para serviços e outros processos do servidor, incluindo w3wp.exe. Você pode resolver o problema executando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em uma conta de administrador ou executando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no console do servidor em vez de uma sessão de Serviços de Terminal. Se nenhuma daquelas soluções alternativas for possível, uma terceira opção é anexar ao processo, executando `vsjitdebugger.exe -p` *ProcessId* da linha de comando do Windows. Você pode determinar a ID do processo usando tlist.exe. Para obter tlist.exe, baixar e instalar as ferramentas de depuração para Windows, disponível em [downloads WDK e WinDbg](http://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a>Cenários comuns de depuração

Para ajudá-lo a identificar se você precisar usar **anexar ao processo** e qual processo para anexar a alguns cenários comuns de depuração são mostrados aqui (a lista não é exaustiva). Onde obter mais instruções estão disponíveis, fornecemos links.

Para alguns tipos de aplicativo (como aplicativos UWP), não conecte diretamente a um nome de processo, mas usar o **depurar pacote do aplicativo instalado** em vez disso, a opção de menu (consulte a tabela).

> [!NOTE]
> Para obter informações sobre como depurar básica no Visual Studio, consulte [guia de Introdução com o depurador](../debugger/getting-started-with-the-debugger.md).

|Cenário|Depurar o método|Nome do Processo|Observações e Links|
|-|-|-|-|
|Depurar um aplicativo gerenciado ou nativo na máquina local|Use anexar ao processo ou [depuração padrão](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|Para acessar rapidamente a caixa de diálogo, use **CTRL + ALT + P** e, em seguida, digite a primeira letra do nome do processo.|
|Depurar aplicativos ASP.NET no computador local após a inicialização do aplicativo sem o depurador|Use anexar ao processo|iiexpress.exe|Isso pode ser útil para tornar seu aplicativo de carregamento mais rápido, como (por exemplo) ao criar o perfil. |
|Depuração remota ASP.NET 4 ou 4.5 em um servidor IIS|Usar as ferramentas remotas e anexar ao processo|W3wp.exe|Consulte [ASP.NET de depuração remota em um computador remoto do IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuração remota ASP.NET Core em um servidor IIS|Usar as ferramentas remotas e anexar ao processo|dotnet.exe|Para implantação de aplicativos, consulte [publicar no IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para depuração, consulte [remoto depuração ASP.NET Core em um computador remoto do IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Depuração de outros tipos de aplicativos com suporte em um processo do servidor|Usar as ferramentas remotas (se o servidor for remoto) e anexar ao processo|outros processos ou iexplore.exe|Se necessário, use o Gerenciador de tarefas para ajudar a identificar o processo. Consulte [depuração remota](../debugger/remote-debugging.md) e seções posteriores neste tópico|
|Um aplicativo de área de trabalho do Windows de depuração remota|F5 e as ferramentas remotas|N/D| Consulte [depuração remota](../debugger/remote-debugging.md)|
|Um aplicativo de UWP (Universal), OneCore, HoloLens e IoT de depuração remota|Depurar pacote do aplicativo instalado|N/D|Consulte [depurar um pacote de aplicativos instalado](debug-installed-app-package.md) em vez de usar **anexar ao processo**|
|Depurar um aplicativo Universal aplicativo UWP (Windows), OneCore, HoloLens e IoT que não tenha iniciado a partir do Visual Studio|Depurar pacote do aplicativo instalado|N/D|Consulte [depurar um pacote de aplicativos instalado](debug-installed-app-package.md) em vez de usar **anexar ao processo**|
  
> [!WARNING]
>  Para anexar a um UWP que está escrito em JavaScript, você primeiro deve ativar a depuração para o aplicativo. Consulte [anexar o depurador](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) no Centro de desenvolvimento do Windows.  
  
> [!NOTE]
>  Para que o depurador se anexe ao código escrito em C++, o código precisa emitir `DebuggableAttribute`. Você pode adicionar isso ao seu código automaticamente por meio da vinculação com a [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) opção de vinculador.

## <a name="what-debugger-features-can-i-use"></a>Quais recursos do depurador pode usar?

Para usar os recursos completos do depurador do Visual Studio (como atingir os pontos de interrupção) ao conectar a um processo, o executável deve corresponder exatamente ao seu local de origem e símbolos (ou seja, o depurador deve ser capaz de carregar o correto [(.pbd) arquivos de símbolo ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Por padrão, isso requer uma compilação de depuração.

Para cenários de depuração remota, você deve ter o código-fonte (ou uma cópia do código-fonte) já aberto no Visual Studio. Os binários do aplicativo compilado no computador remoto devem ser da mesma compilação no computador local.

Em alguns cenários de depuração locais, você pode depurar no Visual Studio sem acesso à fonte de se os arquivos de símbolo correto estiverem presentes com o aplicativo (por padrão, isso requer uma compilação de depuração). Para obter mais informações, consulte [arquivos de origem e especifique o símbolo](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a>Solucionar problemas de erros de conexão  
 Quando o depurador se anexa a um processo em execução, o processo pode conter um ou mais tipos de código. Os tipos de código pode anexar o depurador a são exibidos e selecionados no **Selecionar tipo de código** caixa de diálogo.  
  
 Às vezes, o depurador pode ser anexado com êxito a um tipo de código, mas não a outro tipo de código. Isso pode ocorrer se você estiver tentando anexar a um processo que esteja sendo executado em um computador remoto. O computador remoto pode ter componentes de depuração remota instalados para alguns tipos de código mas não para outros. Isso também pode ocorrer se você tentar anexar a dois ou mais processos para depuração direta de banco de dados. A depuração de SQL dá suporte à anexação de apenas um único processo.  
  
 Se o depurador puder se conectar a alguns, mas não a todos os tipos de código, você verá uma mensagem identificando quais tipos não conseguiram estabelecer conexão.  
  
 Se o depurador for anexado com êxito a pelo menos um tipo de código, você poderá depurar o processo. Você poderá depurar apenas os tipos de código que foram anexados com êxito. A mensagem do exemplo anterior mostra que o tipo de código de script não foi anexado. Portanto, você não pode depurar o código do script dentro do processo. O código de script no processo ainda seria executado, mas você não poderia definir pontos de interrupção, exibir dados ou executar outras operações de depuração no script.  
  
 Se você desejar informações mais específicas sobre por que o depurador não foi anexado a um tipo de código, tente reanexar somente àquele tipo de código.  
  
 **Para obter informações específicas sobre por que um tipo de código falha ao anexar**  
  
1.  Desanexe do processo. Sobre o **depurar** menu, clique em **desanexar tudo**.  
  
2.  Anexe o processo novamente, selecionando apenas um único tipo de código.  
  
    1.  No **anexar ao processo** caixa de diálogo, selecione o processo no **processos disponíveis** lista.  
  
    2.  Clique em **selecione**.  
  
    3.  No **Selecionar tipo de código** caixa de diálogo, selecione **depurar esses tipos de código** e o tipo de código que falha ao anexar. Limpe qualquer outro código.  
  
    4.  Clique em **OK**. O **Selecionar tipo de código** caixa de diálogo é fechada.  
  
    5.  No **anexar ao processo** caixa de diálogo, clique em **Attach**.  
  
     Desta vez, o anexo falhará completamente e você receberá uma mensagem de erro específica.  
  
## <a name="see-also"></a>Consulte também  
 [Vários processos de depuração](../debugger/debug-multiple-processes.md)   
 [Depuração Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depuração remota](../debugger/remote-debugging.md)