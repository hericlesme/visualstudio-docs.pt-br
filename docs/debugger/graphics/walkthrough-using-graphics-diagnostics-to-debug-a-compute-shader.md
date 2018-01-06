---
title: "Passo a passo: Usando diagnóstico de gráficos para depurar um sombreador computado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ef73c45b39c638b2dfc1f88be3323d083efa8493
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Instruções passo a passo: usando diagnóstico de gráficos para depurar um sombreador computado
Este passo a passo demonstra como usar as ferramentas de diagnóstico de gráficos do Visual Studio para investigar um sombreador de computação que gera resultados incorretos.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Usando o **lista de eventos de gráfico** para localizar possíveis fontes do problema.  
  
-   Usando o **pilha de chamadas do evento de gráficos** para determinar qual calcular o sombreador é executado por um DirectCompute `Dispatch` eventos.  
  
-   Usando o **estágios de Pipeline gráficos** janela e HLSL do depurador para examinar o sombreador de computação que é a origem do problema.  
  
## <a name="scenario"></a>Cenário  
 Nesse cenário, você escreveu uma simulação de dinâmica de fluidos que usa DirectCompute para executar as partes com uso intensivo de computação da atualização de simulação. Quando o aplicativo é executado, o processamento de conjunto de dados e da interface do usuário ser correto, mas a simulação não se comportar conforme o esperado. Usando o diagnóstico de gráficos, você pode capturar o problema em um log de elementos gráficos para que você pode depurar o aplicativo. O problema é semelhante a no aplicativo:  
  
 ![O fluidos simulados se comporta incorretamente. ] (media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")  
  
 Para obter informações sobre como detectar os problemas de gráficos em um log de gráficos, consulte [capturando informações de gráficos](capturing-graphics-information.md).  
  
## <a name="investigation"></a>Investigação  
 Você pode usar as ferramentas de diagnóstico de gráficos para carregar o arquivo de log do gráfico para que você pode inspecionar os quadros capturados.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar um quadro em um log de gráficos  
  
1.  No Visual Studio, carregue um log de elementos gráficos que contém um quadro que exibe os resultados de simulação incorreto. Uma nova guia de diagnóstico de gráficos aparece no Visual Studio. Na parte superior dessa guia é a saída de destino de renderização do quadro selecionado. Na parte inferior é parte de **lista quadro**, que exibe uma miniatura de cada quadro capturado.  
  
2.  No **lista quadro**, selecione um quadro que demonstra o comportamento incorreto de simulação. Mesmo que o erro parece ser o código de simulação e não o código de renderização, ainda será necessário escolher um quadro porque DirectCompute eventos são capturados em uma base por quadro, juntamente com eventos Direct3D. Nesse cenário, os gráficos de log guia esta aparência:  
  
     ![Gráficos de registrar o documento no Visual Studio. ] (media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode usar o **lista de eventos de gráfico** para diagnosticar a ele. O **lista de eventos de gráfico** contém um evento para cada chamada DirectCompute e a chamada à API do Direct3D que foi feita durante o quadro ativo — por exemplo, chamadas de API para executar uma computação na GPU ou processar o conjunto de dados ou a interface do usuário. Nesse caso, estamos interessados em `Dispatch` eventos que representam as partes da simulação que são executados na GPU.  
  
#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Para encontrar o evento de envio para a atualização de simulação  
  
1.  No **diagnóstico de gráficos** barra de ferramentas, escolha **lista de eventos** para abrir o **lista de eventos de gráfico** janela.  
  
2.  Inspecione o **lista de eventos de gráfico** para o evento de desenho que renderiza o conjunto de dados. Para facilitar essa tarefa, digite `Draw` no **pesquisa** caixa no canto superior direito do **lista de eventos de gráfico** janela. Isso filtra a lista para que ele contém apenas os eventos que têm "Desenhar" nos títulos. Nesse cenário, você descobrir que eles desenhar eventos ocorreu:  
  
     ![A lista de eventos &#40; EL &#41; mostra desenha eventos. ] (media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")  
  
3.  Percorrer cada evento de desenho enquanto você observa o destino de renderização na guia do documento de log de gráficos.  
  
4.  Interrompa quando o destino de renderização exibe o conjunto de dados processado primeiro. Nesse cenário, o conjunto de dados é processado no primeiro evento de desenho. Erro na simulação é mostrado:  
  
     ![Isso desenhar evento processa o conjunto de dados de simulação. ] (media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")  
  
5.  Agora inspecionar o **lista de eventos de gráfico** para o `Dispatch` eventos que atualiza a simulação. Como é provável que a simulação é atualizada para que seja processado, você pode se concentrar primeiro na `Dispatch` eventos que ocorrem antes do evento de desenho que renderiza os resultados. Para facilitar essa tarefa, modifique o **pesquisa** caixa ler `Draw;Dispatch;CSSetShader(`. Isso filtra a lista para que ele também contém `Dispatch` e `CSSetShader` eventos além dos eventos de desenho. Nesse cenário, você descobre que várias `Dispatch` eventos ocorridos antes do evento de desenho:  
  
     ![Mostra o EL desenhar, eventos de expedição e CSSetShader](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")  
  
 Agora que você sabe que alguns dos potencialmente muitos `Dispatch` eventos podem corresponder ao problema, você pode examiná-los mais detalhadamente.  
  
#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Para determinar qual calcular uma chamada de expedição de sombreador executa  
  
1.  No **diagnóstico de gráficos** barra de ferramentas, escolha **pilha de chamadas do evento** para abrir o **pilha de chamadas do evento de gráficos** janela.  
  
2.  A partir do evento de desenho que renderiza os resultados de simulação, retroceder em cada anterior `CSSetShader` eventos. Em seguida, no **pilha de chamadas do evento de gráficos** janela, escolha a função principal para navegar até o site de chamada. No site de chamada, você pode usar o primeiro parâmetro do [CSSetShader](http://msdn.microsoft.com/library/ff476402.aspx) função chamada para determinar qual calcular o sombreador é executado da próxima `Dispatch` eventos.  
  
 Nesse cenário, há três pares de `CSSetShader` e `Dispatch` eventos em cada quadro. Trabalhando com versões anteriores, a terceira representa de par a integração de etapa (onde as partículas fluidas são realmente movidas), o segundo par representa a etapa de cálculo force (onde força que afetam cada partícula é calculada) e representa o primeiro par de etapa de cálculo de densidade.  
  
#### <a name="to-debug-the-compute-shader"></a>Para depurar o sombreador de computação  
  
1.  No **diagnóstico de gráficos** barra de ferramentas, escolha **estágios do Pipeline** para abrir o **estágios de Pipeline gráficos** janela.  
  
2.  Selecione a terceira `Dispatch` evento (o que precede o evento de emissão) e, em seguida, no **estágios de Pipeline gráficos** janela, sob o **sombreador de cálculo** estágio, escolha  **Iniciar a depuração**.  
  
     ![Selecionando o evento de expedição terceiro no EL.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")  
  
     O depurador HLSL é iniciado no sombreador que executa a etapa de integração.  
  
3.  Examine o código-fonte sombreador computado para a etapa de integração procurar a origem do erro. Quando você usar o diagnóstico de gráficos para depurar o código de computação de sombreador HLSL, você pode percorrer o código e usar outras ferramentas de depuração familiares, como janelas inspecionar. Nesse cenário, você determinar que há não parece ser um erro no sombreador de computação que executa a etapa de integração.  
  
     ![Depurar o sombreador de computação IntegrateCS. ] (media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")  
  
4.  Para parar a depuração do sombreador de computação, no **depurar** barra de ferramentas, escolha **parar depuração** (teclado: Shift + F5).  
  
5.  Em seguida, selecione a segunda `Dispatch` eventos e iniciar a depuração do sombreador de computação, como você fez na etapa anterior.  
  
     ![Selecionar o segundo evento de expedição no EL.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")  
  
     O depurador HLSL é iniciado no sombreador que calcula o força que atuam em cada partícula fluida.  
  
6.  Examine o código-fonte do sombreador computação para a etapa de cálculo de força. Nesse cenário, você determinar que a origem do erro está aqui.  
  
     ![Depuração de ForceCS &#95; Sombreador de cálculo simples. ] (media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")  
  
 Depois de determinar o local do erro, você pode parar a depuração e modificar o código-fonte sombreador computado para calcular corretamente a distância entre as partículas de interação. Nesse cenário, basta alterar a linha `float2 diff = N_position + P_position;` para `float2 diff = N_position - P_position;`:  
  
 ![O computação corrigido &#45; código de sombreador. ] (media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")  
  
 Nesse cenário, porque os sombreadores de computação são compilados no tempo de execução, você pode apenas reiniciar o aplicativo depois de fazer as alterações para observar como eles afetam a simulação. Não é necessário recompilar o aplicativo. Quando você executa o aplicativo, você descobre que agora a simulação funcione corretamente.  
  
 ![O fluidos simulados se comporta corretamente. ] (media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")