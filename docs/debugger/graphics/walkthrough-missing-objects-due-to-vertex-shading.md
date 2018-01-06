---
title: "Passo a passo: Objetos ausentes devido ao sombreamento de vértice | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f374bbbdf30a80bdea70b789da5d5febbeee7a82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Instruções passo a passo: objetos ausentes devido ao sombreamento de vértice
Este passo a passo demonstra como usar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ferramentas de diagnóstico de gráficos para investigar um objeto que está faltando devido a um erro que ocorre durante o estágio de sombreador de vértice.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Usando o **lista de eventos de gráfico** para localizar possíveis fontes do problema.  
  
-   Usando o **estágios de Pipeline gráficos** janela para verificar o efeito do `DrawIndexed` chamadas à API do Direct3D.  
  
-   Usando o **depurador HLSL** para examinar o sombreador de vértice.  
  
-   Usando o **pilha de chamadas do evento de gráficos** para ajudar a localizar a origem de uma constante HLSL incorretova.  
  
## <a name="scenario"></a>Cenário  
 Uma das causas comuns de um objeto ausente em um aplicativo 3D ocorre quando o sombreador de vértice transforma vértices do objeto de modo incorreto ou inesperado — por exemplo, o objeto pode ser dimensionado para um tamanho muito pequeno ou transformado, de modo que ela apareça atrás da câmera , em vez de na frente dele.  
  
 Nesse cenário, quando o aplicativo é executado para testá-lo, o plano de fundo é renderizado conforme o esperado, mas um dos objetos não aparecem. Usando o diagnóstico de gráficos, você capturar o problema em um log de elementos gráficos para que você pode depurar o aplicativo. O problema é semelhante a no aplicativo:  
  
 ![O objeto não pode ser visto. ] (media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")  
  
## <a name="investigation"></a>Investigação  
 Usando as ferramentas de diagnóstico de gráficos, você pode carregar o arquivo de log do gráfico para inspecionar os quadros que foram capturados durante o teste.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar um quadro em um log de gráficos  
  
1.  Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregar um log de elementos gráficos que contém um quadro que exibe o objeto ausente. Uma nova guia log gráficos aparece no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Na parte superior dessa guia é a saída de destino de renderização do quadro selecionado. Na parte inferior é parte de **lista quadro**, que exibe cada quadro capturado como uma imagem em miniatura.  
  
2.  No **lista quadro**, selecione um quadro que demonstra que o objeto não será exibido. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, os gráficos de log guia esta aparência:  
  
     ![Gráficos de registrar o documento no Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode começar a diagnosticá-lo usando o **lista de eventos de gráfico**. O **lista de eventos de gráfico** contém todas as chamadas de API do Direct3D que foi feita para renderizar o quadro ativo, por exemplo, chamadas de API para configurar o estado do dispositivo, para criar e atualizar buffers e desenhar objetos que aparecem no quadro. Muitos tipos de chamadas são interessantes porque não há normalmente (mas nem sempre) uma alteração correspondente no destino de renderização quando o aplicativo está funcionando conforme o esperado, por exemplo desenhar, expedição, cópia ou desmarque chamadas. Chamadas de desenho são especialmente interessantes porque cada um deles representa geometria que o aplicativo renderizado (chamadas de expedição também podem processar a geometria).  
  
 Porque você sabe que o objeto ausente não desenhado para o destino de renderização (neste caso) —, mas que o restante da cena é desenhado como esperado — você pode usar o **lista de eventos de gráfico** junto com o **Pipeline gráficos Estágios** tool para determinar qual desenhar chamada corresponde a geometria do objeto ausente. O **estágios de Pipeline gráficos** janela mostra a geometria que foi enviada para cada chamada de desenho, independentemente de seu efeito sobre o destino de renderização. Como você percorrer as chamadas de desenho, que os estágios de pipeline são atualizados para mostrar a geometria que está associada essa chamada, e a saída de destino de renderização é atualizada para mostrar o estado de destino de renderização depois que a chamada foi concluída.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Para localizar a chamada de desenho de geometria ausente  
  
1.  Abra o **lista de eventos de gráfico** janela. Sobre o **diagnóstico de gráficos** barra de ferramentas, escolha **lista de eventos**.  
  
2.  Abra o **estágios de Pipeline gráficos** janela. Sobre o **diagnóstico de gráficos** barra de ferramentas, escolha **estágios do Pipeline**.  
  
3.  Quando você percorre cada desenhar chamada no **lista de eventos de gráfico** janela, inspecionar o **estágios de Pipeline gráficos** janela para o objeto ausente. Para facilitar essa tarefa, digite "Desenhar" no **pesquisa** caixa no canto superior direito do **lista de eventos de gráfico** janela. Isso filtra a lista para que ele contém apenas os eventos que têm "Desenhar" nos títulos.  
  
     No **estágios de Pipeline gráficos** janela, o **Assembler de entrada** estágio mostra a geometria do objeto antes transformados e o **sombreador de vértice** estágio mostra a mesma objeto depois que ele é transformado. Nesse cenário, você sabe que encontramos do objeto quando ele for exibido no **Assembler de entrada** estágio e nada é exibido no **sombreador de vértice** estágio.  
  
    > [!NOTE]
    >  Se outros estágios de geometria — por exemplo, os estágios de sombreador de envoltório, sombreador de domínio ou Geometry Shader — processar o objeto, eles podem ser a causa do problema. Normalmente, o problema está relacionado ao estágio anterior em que o resultado não é exibido ou é exibido de forma inesperada.  
  
4.  Pare quando chegar a chamada de desenho que corresponde ao objeto ausente. Nesse cenário, o **estágios de Pipeline gráficos** janela indica que a geometria foi emitida para a GPU (indicada pela miniatura Assembler de entrada), mas não aparecem no destino de renderização porque algo deu errado durante a estágio de sombreador de vértice (indicado pela miniatura sombreador de vértice):  
  
     ![Um evento DrawIndexed e seu efeito sobre o pipeline](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")  
  
 Depois de confirmar que o aplicativo emitiu uma chamada de desenho para geometria do objeto ausente e descobrir que o problema ocorre durante o estágio de sombreador de vértice, você pode usar o depurador HLSL para examinar o sombreador de vértice e descobrir o que aconteceu com a geometria do objeto. Você pode usar o depurador HLSL para examinar o estado das variáveis HLSL durante a execução, percorrer o código HLSL e definir pontos de interrupção para ajudá-lo a diagnosticar o problema.  
  
#### <a name="to-examine-the-vertex-shader"></a>Para examinar o sombreador de vértice  
  
1.  Inicie a depuração o estágio de sombreador de vértice. No **estágios de Pipeline gráficos** janela, sob o **sombreador de vértice** estágio, escolha o **iniciar depuração** botão.  
  
2.  Porque o **Assembler de entrada** estágio é exibido fornecer dados para o sombreador de vértice e o **sombreador de vértice** estágio é exibida não produzir nenhuma saída, você deseja examinar a saída do sombreador de vértice estrutura, `output`. Como percorrer o código HLSL, você levar perto pesquisar quando `output` é modificado.  
  
3.  Na primeira vez que `output` for modificado, o membro `worldPos` é gravado.  
  
     ![O valor de "output.worldPos" aparece razoável](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")  
  
     Como seu valor parece ser razoável, você continuar percorrendo o código até a próxima linha que modifica `output`.  
  
4.  Na próxima vez que `output` for modificado, o membro `pos` é gravado.  
  
     ![O valor de "output.pos" foi zerado](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")  
  
     Neste momento, o valor de `pos` membro — todos os zeros — parecer suspeito. Em seguida, você deseja determinar como `output.pos` fornecida para ter um valor de zeros.  
  
5.  Observe que `output.pos` leva seu valor de uma variável denominada `temp`. Na linha anterior, verá que o valor de `temp` é o resultado da multiplicação seu valor anterior por uma constante chamada `projection`. Você suspeita que `temp`do valor suspeita é o resultado dessa multiplicação. Quando você posiciona o ponteiro no `projection`, você notar que seu valor é também todos os zeros.  
  
     ![A matriz de projeção contém uma transformação incorreta](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")  
  
     Nesse cenário, a análise revela que `temp`do valor suspeita é provavelmente causado por seu multiplicação por `projection`e porque `projection` é uma constante que tem devem conter uma matriz de projeção, você sabe que não deveria contém todos os zeros.  
  
 Depois de determinar que a constante HLSL `projection`— passado para o sombreador pelo seu aplicativo — é a origem provável do problema, a próxima etapa é para encontrar o local no código-fonte do seu aplicativo onde o buffer de constantes é preenchido. Você pode usar o **pilha de chamadas do evento de gráficos** para localizar esse local.  
  
#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Para localizar onde a constante é definida no código-fonte do aplicativo  
  
1.  Abra o **pilha de chamadas do evento de gráficos** janela. Sobre o **diagnóstico de gráficos** barra de ferramentas, escolha **pilha de chamadas do evento de gráficos**.  
  
2.  Navegar na pilha de chamada no código-fonte do seu aplicativo. No **pilha de chamadas do evento de gráficos** janela, escolha a chamada mais alto para ver se o buffer de constantes preenchimento existe. Se não estiver, continue a pilha de chamadas até encontrar onde é preenchido. Nesse cenário, você descobre que o buffer de constantes está sendo preenchido — usando o `UpdateSubresource` API do Direct3D — mais acima a pilha de chamadas em uma função chamada `MarbleMaze::Render`, e seu valor é proveniente de um objeto de buffer constante chamada `m_marbleConstantBufferData` :  
  
     ![O código que define o buffer de constantes do objeto](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")  
  
    > [!TIP]
    >  Se simultaneamente depurar seu aplicativo, você pode definir um ponto de interrupção neste local e será atingido quando o próximo quadro é processado. Em seguida, você poderá inspecionar os membros de `m_marbleConstantBufferData` para confirmar que o valor da `projection` membro é definido para todos os zeros quando o buffer de constantes é preenchido.  
  
 Depois de encontrar o local onde o buffer de constantes está sendo preenchido e descobrir que seus valores provenientes da variável `m_marbleConstantBufferData`, a próxima etapa é descobrir onde o `m_marbleConstantBufferData.projection` membro é definido para todos os zeros. Você pode usar **localizar todas as referências** para verificar rapidamente para o código que altera o valor de `m_marbleConstantBufferData.projection`.  
  
#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Para localizar onde o membro de projeção é definido no código-fonte do aplicativo  
  
1.  Localizar referências para `m_marbleConstantBufferData.projection`. Abra o menu de atalho para a variável `m_marbleConstantBufferData`e, em seguida, escolha **localizar todas as referências**.  
  
2.  Para navegar até o local da linha no código-fonte do seu aplicativo onde o `projection` membro será modificado, escolha a linha no **localizar resultados de símbolos** janela. Como o primeiro resultado que modifica o membro de projeção não pode ser a causa do problema, você terá que examinar várias áreas do código-fonte do seu aplicativo.  
  
 Depois de encontrar o local onde `m_marbleConstantBufferData.projection` estiver definido, você pode examinar o código ao redor do código-fonte para determinar a origem do valor incorreto. Nesse cenário, você descobre que o valor de `m_marbleConstantBufferData.projection` é definido como uma variável local denominada `projection` antes que ela foi inicializada como um valor que é fornecido pelo código `m_camera->GetProjection(&projection);` na próxima linha.  
  
 ![A projeção marble está definida antes da inicialização](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")  
  
 Para corrigir o problema, você move a linha de código que define o valor de `m_marbleConstantBufferData.projection` após a linha que inicializa o valor da variável local `projection`.  
  
 ![Corrigido C# 43; &#43; código-fonte](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")  
  
 Depois de corrigir o código, você poderá recriá-lo e executar o aplicativo novamente para descobrir se o problema de renderização é resolvido:  
  
 ![O objeto agora é exibido. ] (media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")