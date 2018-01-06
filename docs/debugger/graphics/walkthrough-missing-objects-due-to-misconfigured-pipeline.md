---
title: 'Passo a passo: Objetos ausentes devido ao Pipeline configurado incorretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8b6809f3238c4d239d6d07f0df35d9b4a035d945
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Instruções passo a passo: objetos ausentes devido ao pipeline configurado incorretamente
Este passo a passo demonstra como usar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ferramentas de diagnóstico de gráficos para investigar um objeto que está faltando devido a um sombreador de pixel não definida.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Usando o **lista de eventos de gráfico** para localizar possíveis fontes do problema.  
  
-   Usando o **estágios de Pipeline gráficos** janela para examinar o efeito do `DrawIndexed` chamada à API do Direct3D.  
  
-   Inspecionando o contexto de dispositivo para confirmar que um estágio do sombreador não foi definido.  
  
-   Usando o **estágios de Pipeline gráficos** janela junto com o **pilha de chamadas do evento de gráficos** para ajudar a localizar a origem do sombreador de pixel não definida.  
  
## <a name="scenario"></a>Cenário  
 Quando um objeto está ausente em um aplicativo 3D, às vezes, é porque um dos estágios de sombreador não está definido para que o objeto é processado. Em aplicativos que têm necessidades de processamento simples, a origem do erro é geralmente localizada em algum lugar na pilha de chamadas de chamada de desenho do objeto. No entanto, como uma otimização, alguns objetos de lote juntos de aplicativos com programas de sombreador, texturas ou outros dados em comum para minimizar a alteração de estadom sobrecarga. Nesses aplicativos, a origem do erro pode ser inserida no sistema de envio em lote, em vez de localizado na pilha de chamadas da chamada de desenho. O cenário neste passo a passo demonstra um aplicativo que precisa de processamento simples e portanto a origem do erro pode ser encontrada na pilha de chamadas.  
  
 Nesse cenário, quando o aplicativo é executado para testá-lo, o plano de fundo é renderizado conforme o esperado, mas um dos objetos não aparece. Usando o diagnóstico de gráficos, você capturar o problema em um log de elementos gráficos para que você pode depurar o aplicativo. O problema é semelhante a no aplicativo:  
  
 ![O objeto não pode ser visto](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")  
  
## <a name="investigation"></a>Investigação  
 Usando as ferramentas de diagnóstico de gráficos, você pode carregar o documento de log de gráficos para inspecionar os quadros que foram capturados durante o teste.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar um quadro em um log de gráficos  
  
1.  Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregar um documento de log de elementos gráficos que contém um quadro que exibe o objeto ausente. Uma nova guia log gráficos aparece no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Na parte superior dessa guia é a saída de destino de renderização do quadro selecionado. Na parte inferior é parte de **lista quadro**, que exibe cada quadro capturado como uma imagem em miniatura.  
  
2.  No **lista quadro**, selecione um quadro que demonstra que o objeto não será exibido. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, os gráficos de log guia esta aparência:  
  
     ![Gráficos de registrar o documento no Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode começar a diagnosticá-lo usando o **lista de eventos de gráfico**. O **lista de eventos de gráfico** contém todas as chamadas de API do Direct3D renderizar o quadro ativo — por exemplo, para configurar o estado do dispositivo, para criar e atualizar buffers e desenhar objetos que aparecem no quadro. Muitos tipos de chamadas — por exemplo, desenho, expedição, cópia ou desmarque chamadas — são interessantes porque não há normalmente (mas nem sempre) uma alteração correspondente no destino de renderização quando o aplicativo está funcionando conforme o esperado. Chamadas de desenho são especialmente interessantes porque cada um deles representa geometria que o aplicativo processado.  
  
 Porque você sabe que o destino de renderização não contém a falta de objeto mas também que não parece haver outros erros, você pode usar o **lista de eventos de gráfico** junto com o **estágios de Pipeline gráficos**tool para determinar qual desenhar chamada corresponde a geometria do objeto ausente. O **estágios de Pipeline gráficos** janela mostra a geometria que foi enviada para cada chamada de desenho, independentemente de seu efeito sobre o destino de renderização. Como percorrer as chamadas de desenho, os estágios de pipeline são atualizados para mostrar a geometria associada a cada chamada conforme ela flui através de cada estágio habilitado e a saída de destino de renderização é atualizada para mostrar o estado de destino de renderização depois da chamada ser concluída.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Para localizar a chamada de desenho de geometria ausente  
  
1.  Abra o **lista de eventos de gráfico** janela. Sobre o **diagnóstico de gráficos** barra de ferramentas, escolha **lista de eventos**.  
  
2.  Abra o **estágios de Pipeline gráficos** janela. Sobre o **diagnóstico de gráficos** barra de ferramentas, escolha **estágios do Pipeline**.  
  
3.  Quando você percorre cada desenhar chamada no **lista de eventos de gráfico** janela, inspecionar o **estágios de Pipeline gráficos** janela para o objeto ausente. Para facilitar essa tarefa, digite "Desenhar" no **pesquisa** caixa no canto superior direito do **lista de eventos de gráfico** janela. Isso filtra a lista para que ele contém apenas os eventos que têm "Desenhar" nos títulos.  
  
     No **estágios de Pipeline gráficos** janela, o **Assembler de entrada** estágio mostra a geometria do objeto antes que ele é transformado e o **sombreador de vértice** estágio mostra a mesma objeto depois que ele é transformado. Nesse cenário, observe que o **estágios de Pipeline gráficos** janela mostra o **Assembler de entrada** e **sombreador de vértice** prepara, mas não o **sombreador de Pixel**  estágio para uma das chamadas de desenho.  
  
    > [!NOTE]
    >  Se outros estágios de pipeline — por exemplo, o sombreador de envoltório, sombreador de domínio ou estágios de sombreador de geometria, processar o objeto, qualquer um deles pode ser a causa do problema. Normalmente, o problema está relacionado ao estágio anterior em que o resultado não é exibido ou é exibido de forma inesperada.  
  
4.  Pare quando chegar a chamada de desenho que corresponde ao objeto ausente. Nesse cenário, o **estágios de Pipeline gráficos** janela indica que a geometria foi emitida para a GPU (indicado pela presença do **Assembler de entrada** estágio) e transformados (indicado pelo  **Sombreador de vértice** estágio), mas não aparece no destino de renderização porque não parece ser um sombreador de pixel active (indicado pela ausência do **sombreador de Pixel** estágio). Nesse cenário, você pode até ver a silhueta do objeto ausente no **fusão de saída** estágio:  
  
     ![Um evento DrawIndexed e seu efeito sobre o pipeline](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")  
  
 Depois de confirmar que o aplicativo emitiu uma chamada de desenho para geometria do objeto ausente e descobrir que o estágio de sombreador de pixel estava inativo, você pode examinar o estado do dispositivo para confirmar suas descobertas. Você pode usar o **tabela de objetos gráficos** para examinar o contexto de dispositivo e outros dados de objeto do Direct3D.  
  
#### <a name="to-examine-device-context"></a>Para examinar o contexto de dispositivo  
  
1.  Abra o **o contexto de dispositivo d3d11**. No **estágios de Pipeline gráficos** janela, escolha o **ID3D11DeviceContext** link que faz parte do `DrawIndexed` chamada que é exibida na parte superior da janela.  
  
2.  Examine o estado do dispositivo que é exibido no **o contexto de dispositivo d3d11** tab para confirmar que nenhum sombreador de pixel estava ativo durante a chamada de desenho. Nesse cenário, o **informações gerais do sombreador**— exibido em **estado de sombreador de pixel**— indica que o sombreador está **nulo**:  
  
     ![O contexto de dispositivo D3D 11 mostra o estado de sombreador de pixel](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")  
  
 Depois de confirmar que o sombreador de pixel foi definido como nulo pelo seu aplicativo, a próxima etapa é encontrar o local no código-fonte do seu aplicativo onde o sombreador está definido. Você pode usar o **lista de eventos de gráfico** junto com o **pilha de chamadas do evento de gráficos** para localizar esse local.  
  
#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Para localizar onde o sombreador de pixel é definido no código-fonte do aplicativo  
  
1.  Localizar o `PSSetShader` chamada que corresponde ao objeto ausente. No **lista de eventos de gráfico** janela, digite "desenhado. PSSetShader"no **pesquisa** caixa no canto superior direito do **lista de eventos de gráfico** janela. Isso filtra a lista para que ele contém apenas os eventos de "PSSetShader" e que têm "Desenhar" nos títulos. Escolha o primeiro `PSSetShader` chamada que aparece antes da chamada de desenho do objeto ausente.  
  
    > [!NOTE]
    >  `PSSetShader`não aparecerá no **lista de eventos de gráfico** janela se ela não foi definida durante esse período. Normalmente isso ocorre apenas se o sombreador de pixel apenas uma é usada para todos os objetos, ou se o `PSSetShader` chamada acidentalmente foi ignorada durante esse período. Em ambos os casos, é recomendável que você procurar o código-fonte do aplicativo para `PSSetShader` chamadas e use tradicional de técnicas de depuração para examinar o comportamento dessas chamadas.  
  
2.  Abra o **pilha de chamadas do evento de gráficos** janela. Sobre o **diagnóstico de gráficos** barra de ferramentas, escolha **pilha de chamadas do evento de gráficos**.  
  
3.  Use a pilha de chamadas para localizar o `PSSetShader` chamada no código-fonte do seu aplicativo. No **pilha de chamadas do evento de gráficos** janela, escolha a chamada mais alto e examine o valor que o sombreador de pixel está sendo definido como. Sombreador de pixel pode ser definido diretamente como nulo ou null pode ocorrer devido a um argumento que foi passado para a função ou outro estado. Se não estiver definido diretamente, você poderá localizar a origem do valor nulo em algum lugar a pilha de chamadas. Nesse cenário, você descobrir que o sombreador de pixel está sendo definido diretamente para `nullptr` na função principal, que é chamado `CubeRenderer::Render`:  
  
     ![O código que não inicializar o sombreador de pixel](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")  
  
    > [!NOTE]
    >  Se você não puder localizar a origem do valor nulo apenas por meio do exame da pilha de chamadas, recomendamos que você defina um ponto de interrupção condicional no `PSSetShader` chamar, de modo que a execução do programa quebra quando o sombreador de pixel será definido como null. Em seguida, reinicie o aplicativo no modo de depuração e usar técnicas tradicionais de depuração para localizar a fonte do valor nulo.  
  
 Para corrigir o problema, atribua o sombreador de pixel correto usando o primeiro parâmetro do `ID3D11DeviceContext::PSSetShader` chamada à API.  
  
 ![Corrigido C# 43; &#43; código-fonte](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")  
  
 Depois de corrigir o código, você poderá recriá-lo e executar o aplicativo novamente para verificar se o problema de renderização é resolvido:  
  
 ![O objeto é exibido agora](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")