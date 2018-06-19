---
title: Atrasa a diagnosticar a extensão da interface do usuário no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: douge
ms.workload: multiple
ms.openlocfilehash: b63f9538c916b74874031704a1f60d0646f8d032
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134326"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Como: diagnosticar UI atrasos causados pelas extensões

Quando a interface do usuário se torna sem resposta, o Visual Studio examina a pilha de chamadas do thread da interface do usuário, começando com a folha e funcionando em direção a base. Se o Visual Studio determina que um quadro de pilha de chamadas pertence a um módulo que faz parte de uma extensão de instalado e habilitada, ele mostrará uma notificação.

![Atraso de interface do usuário (falta de resposta) notificação](media/ui-delay-notification-in-vs.png)

A notificação informa ao usuário que o atraso de interface do usuário (ou seja, a falta de resposta na interface de usuário) pode ter sido o resultado do código da extensão. Ele também fornece o usuário com opções para desabilitar a extensão ou futuras notificações para essa extensão.

Este documento descreve como diagnosticar o que em seu código de extensão está causando notificações de atraso de interface do usuário. 

> [!NOTE]
> Não use a instância experimental do Visual Studio para diagnosticar atrasos de interface do usuário. Algumas partes da análise de pilha de chamada necessária para notificações de atraso de interface do usuário são desativadas ao usar a instância experimental, que significa que as notificações de atraso de interface do usuário não podem ser mostradas.

Uma visão geral do processo de diagnóstico é o seguinte:
1. Identifique o cenário de gatilho.
2. Reinicie o VS com atividade de logon.
3. Inicie o rastreamento ETW.
4. Disparar a notificação aparecer novamente.
5. Pare o rastreamento ETW.
6. Examine o log de atividades para obter a ID de atraso.
7. Analise o rastreamento ETW usando uma ID de atraso da etapa 6.

As seções a seguir, veremos essas etapas em mais detalhes.

## <a name="identifying-the-trigger-scenario"></a>Identificando o cenário de gatilho

Para diagnosticar um atraso de interface do usuário, você primeiro precisa identificar quais (sequência de ações) faz com que o Visual Studio para mostrar a notificação. Isso está na ordem para que você pode disparar a notificação posteriormente com o log ativado.

## <a name="restarting-vs-with-activity-logging-on"></a>Reiniciar VS com atividade de logon

O Visual Studio pode gerar um log de atividades"" que fornece informações úteis ao depurar um problema. Para ativar a atividade de registro em log no Visual Studio, inicie o Visual Studio com o `/log` opção de linha de comando. Depois que o Visual Studio inicia, o log de atividades é armazenado no seguinte local:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Para saber mais sobre como você pode encontrar os VS ID da instância, consulte [ferramentas para detectar e gerenciar instâncias do Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Posteriormente, usaremos o log de atividades para obter mais informações sobre as notificações relacionadas e de atrasos da interface do usuário.

## <a name="starting-etw-tracing"></a>Iniciar o rastreamento ETW

Você pode usar [PerfView](https://github.com/Microsoft/perfview/) para coletar um rastreamento ETW. PerfView fornece uma interface fácil de usar para coletar um rastreamento ETW e analisá-los. Use o comando a seguir para coletar um rastreamento:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Isso permite que o provedor "Microsoft VisualStudio", que é o que Visual Studio usa para eventos relacionados a notificações de atraso de interface do usuário. Ela também especifica a palavra-chave para o provedor de kernel PerfView pode usar para gerar a exibição "Thread pilhas de tempo".

## <a name="triggering-the-notification-to-appear-again"></a>Disparar a notificação aparecer novamente

Após o início PerfView coleta de rastreamento, você pode usar a sequência de ação de gatilho (da etapa 1) para a notificação aparecer novamente. Assim que a notificação é exibida, você pode parar a coleta de rastreamento para PerfView processar e gerar o arquivo de rastreamento de saída.

## <a name="stopping-etw-tracing"></a>Interrompendo o rastreamento ETW

Para interromper a coleta de rastreamento, basta usar o `Stop collection` botão na janela PerfView. Depois de parar a coleta de rastreamento, PerfView automaticamente processará os eventos ETW e gera um arquivo de rastreamento de saída.

## <a name="examining-the-activity-log-to-get-the-delay-id"></a>Examinando o log de atividades para obter a ID de atraso

Como mencionado anteriormente, você pode encontrar o log de atividades em `%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml`. Toda vez que o Visual Studio detecta uma extensão de atraso de interface do usuário, ele grava um nó para o log de atividades com `UIDelayNotifications` como a origem. Esse nó contém quatro partes de informações sobre o atraso de interface do usuário:

- A ID de atraso de interface do usuário, um número sequencial que identifica exclusivamente um atraso de interface do usuário em uma sessão do VS
- A ID de sessão, que identifica exclusivamente a sessão do Visual Studio do início ao fechar
- Se uma notificação foi mostrada para o atraso de interface do usuário
- A extensão que provavelmente causado o atraso de interface do usuário

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Nem todos os resultados de atrasos da interface do usuário em uma notificação. Portanto, sempre verifique se o "notificação mostrada?" valor para identificar corretamente o atraso de interface do usuário à direita.

Depois de localizar o atraso de interface do usuário correto no log de atividades, anote a ID de atraso de interface do usuário especificada no nó. Você usará a ID para procurar o evento ETW correspondente na próxima etapa.

## <a name="analyzing-the-etw-trace"></a>Analisar o rastreamento ETW

Em seguida, abra o arquivo de rastreamento. Você pode fazer isso usando a mesma instância de PerfView ou iniciar uma nova instância e definindo o caminho da pasta atual no canto superior esquerdo da janela para o local do arquivo de rastreamento.

![Definir o caminho da pasta no Perfview](media/perfview-set-path.png)

Em seguida, selecione o arquivo de rastreamento no painel esquerdo e abri-la clicando em Abrir no menu de contexto ou o botão direito do mouse.

> [!NOTE]
> Por padrão o PerfView gera um arquivo Zip. Quando você abre trace.zip, ele automaticamente descompacta o arquivo e abre o rastreamento. Você pode ignorar isso desmarcando a caixa "Zip" durante a coleta de rastreamento. No entanto, se você pretende transferir e usar rastreamento em máquinas diferentes, convém desmarcando a caixa "Zip". Sem essa opção, os PDBs necessárias para assemblies Ngen não acompanhará o rastreamento e, portanto, símbolos de assemblies Ngen não serão resolvidos no computador de destino. (Consulte [esta postagem de blog](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) para obter mais informações sobre PDBs para assemblies Ngen.) 

Pode levar vários minutos para PerfView processar e abrir o rastreamento. Quando o rastreamento é aberto, uma lista de exibições de vários"" aparecem sob ele.

![Exibição de resumo de rastreamento PerfView](media/perfview-summary-view-events-selected.png)

Primeiro, usaremos o modo de exibição "Eventos" para obter o intervalo de tempo do atraso da interface do usuário:

1. Abra o modo de exibição "Eventos" selecionando o nó de "Eventos" no rastreamento e escolhendo abrir no menu de contexto ou o botão direito do mouse.
2. Selecione "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" no painel esquerdo.
3. Pressione Enter

A seleção é aplicada e todos os `ExtensionUIUnresponsiveness` eventos são exibidos no painel direito.

![A seleção de eventos no modo de exibição de eventos](media/perfview-event-selection.png)

Cada linha no painel direito corresponde a um atraso de interface do usuário. O evento inclui um valor de "Atraso ID" que deve corresponder ao identificador de atraso no log de atividades da etapa 6. Como `ExtensionUIUnresponsiveness` é acionado no final do atraso da interface do usuário, o carimbo de hora do evento (aproximadamente) marcas a hora de término do atraso da interface do usuário. O evento também contém a duração do atraso. Podemos pode subtrair a duração do carimbo de hora de término para obter o carimbo de hora de quando o atraso de interface do usuário é iniciada.

![Calcular o intervalo de tempo do atraso da interface do usuário](media/ui-delay-time-range.png)

A captura de tela anterior, por exemplo, o carimbo de hora do evento é 12,125.679 e a duração do atraso é 6,143.085 (ms). Assim,
* O atraso de início é 12,125.679 6,143.085 = 5,982.594.
* O intervalo de tempo de atraso de interface do usuário é 5,982.594 para 12,125.679.

Assim que tivermos o intervalo de tempo, podemos fechar o modo de exibição de eventos e abra a exibição "Pilhas de Thread tempo (com atividades StartStop)". Esta exibição é especialmente útil porque geralmente as extensões que estão bloqueando o thread de interface do usuário são simplesmente aguardando outros threads ou uma operação vinculada à e/S. Assim, o modo de exibição "Pilha de CPU", que é a opção ideal para a maioria dos casos, não pode capturar o tempo que o thread gasta desde que ele não está usando a CPU durante esse período de bloqueio. "Thread tempo pilhas" resolve esse problema quando corretamente mostrando bloqueado.

![Nó de pilhas de tempo (com atividades StartStop) do thread no modo de exibição de resumo de PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Ao abrir "Thread pilhas de tempo" Exibir, escolha o processo de "devenv" para iniciar a análise.

![Exibição de pilhas de tempo para análise de atraso de interface do usuário do thread](media/ui-delay-thread-time-stacks.png)

No modo de exibição "Thread pilhas de tempo", no canto superior esquerdo da página, você pode definir o intervalo de tempo para os valores calculado na etapa anterior e pressione Enter para que as pilhas são ajustadas para esse intervalo de tempo.

> [!NOTE]
> Determinar qual thread é a interface do usuário thread (inicialização) pode ser intuitiva se a coleta de rastreamento é iniciada depois que o Visual Studio já está aberto. No entanto, os primeiros elementos na pilha do thread da interface do usuário (inicialização) são mais provável sempre DLLs do sistema operacional (ntdll.dll e Kernel32) seguidos de devenv!? e, em seguida, msenv!?. Esta sequência pode ajudar a identificar o thread de interface do usuário.

 ![Identificando o thread de inicialização](media/ui-delay-startup-thread.png)

Você também pode filtrar este modo de exibição somente incluindo pilhas que contêm os módulos do seu pacote.

* Defina "GroupPats" como texto vazio para remover qualquer agrupamento adicionado por padrão.
* Conjunto "IncPats" para incluir a parte de seu nome de assembly, além de filtro de processo existente. Nesse caso, ele deve ser "devenv; UIDelayR2 ".

![Definir GroupPath e IncPath no modo de pilhas de Thread de tempo](media/perfview-tts-group-path-inc-path.png)

PerfView tem detalhadas orientação sob o menu de Ajuda que você pode usar para identificar afunilamentos de desempenho no seu código. Além disso, os links a seguir fornecem mais informações sobre como utilizar o Visual Studio threading de APIs para otimizar seu código:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

Você também pode usar os novo analisadores estáticos do Visual Studio para extensões (pacote do NuGet [aqui](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), que fornecem orientação sobre as práticas recomendadas para escrever extensões eficientes. Consulte uma lista de [analisadores de SDK do VS](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) e [threading analisadores](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Se não for possível resolver a falta de resposta devido a dependências você não tem controle sobre (por exemplo, se sua extensão precisa chamar serviços de VS síncronos no thread da interface do usuário), gostaríamos de saber sobre ele. Se você for um membro de nosso programa de parceiro do Visual Studio, você pode contatar nos enviando uma solicitação de suporte do desenvolvedor. Caso contrário, use a ferramenta de um problema de relatório para enviar seus comentários e incluir `"Extension UI Delay Notifications"` no título. Também inclua uma descrição detalhada da sua análise.
