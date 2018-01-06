---
title: "Passo a passo: Depurando erros devido ao sombreamento de renderização | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 55638339935639c5d7bcb726f981b7edecdcadca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Instruções passo a passo: depurando erros de renderização devido ao sombreamento
Este passo a passo demonstra como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnóstico de gráficos para investigar um objeto que é colorido incorretamente devido a um bug de sombreador.  
  
 Este passo a passo demonstra como:  
  
-   Examine o documento de log de gráficos para identificar os pixels que mostram o problema.  
  
-   Use o **histórico de Pixel gráfico** janela para examinar o estado de pixel mais de perto.  
  
-   Use o **depurador HLSL** para examinar os sombreadores de pixel e vértice.  
  
## <a name="scenario"></a>Cenário  
 Cores incorreto em objetos normalmente ocorre quando um sombreador de vértice passa um pixel informações incorreta ou incompleta do sombreador.  
  
 Nesse cenário, você adicionou recentemente um objeto ao seu aplicativo, junto com o novo vértice e sombreadores de pixel para transformar o objeto e dê a ele uma aparência exclusiva. Quando você executa o aplicativo durante um teste, o objeto é processado em preto sólido. Usando o diagnóstico de gráficos, você capturar o problema em um log de elementos gráficos para que você pode depurar o aplicativo. O problema é semelhante a no aplicativo:  
  
 ![O objeto é processado com cores incorretas. ] (media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")  
  
## <a name="investigation"></a>Investigação  
 Usando as ferramentas de diagnóstico de gráficos, você pode carregar o documento de log de gráficos para inspecionar os quadros que foram capturados durante o teste.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar um quadro em um log de gráficos  
  
1.  Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregar um log de elementos gráficos que contém um quadro que exibe o modelo ausente. Uma nova janela de documento do log do gráfico aparece no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Na parte superior da janela é a saída de destino de renderização do quadro selecionado. Na parte inferior é parte de **lista quadro**, que exibe cada quadro capturado como uma imagem em miniatura.  
  
2.  No **lista quadro**, selecione um quadro no qual o objeto não tem a aparência correta. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, os gráficos log documento janela esta aparência:  
  
     ![Gráficos de registrar o documento no Visual Studio. ] (media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode usar o **histórico de Pixel gráfico** janela para diagnosticar a ele. O **histórico de Pixel gráfico** janela mostra os primitivos que podem ter tido um efeito em um pixel específico, seus sombreadores e quais seus efeitos sobre o destino de renderização são, em ordem cronológica.  
  
#### <a name="to-examine-a-pixel"></a>Para examinar um pixel  
  
1.  Abra o **histórico de Pixel gráfico** janela. Sobre o **diagnóstico de gráficos** barra de ferramentas, escolha **histórico de Pixel**.  
  
2.  Selecione um pixel para examinar. Na janela de documento do log de gráficos, selecione um dos pixels no objeto que é colorido incorretamente:  
  
     ![Selecionar um pixel exibe informações sobre seu histórico. ] (media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")  
  
     O **histórico de Pixel gráfico** janela é atualizada para refletir o pixel selecionado. Nesse cenário, o **histórico de Pixel gráfico** janela tem esta aparência:  
  
     ![O histórico de pixel mostra um evento DrawIndexed. ] (media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")  
  
     Observe que o resultado do sombreador de pixel é completamente opaco preto (0, 0, 0, 1) e que o **fusão de saída** combinado com o **anterior** cor do pixel de forma que o **resultados** também é opaco totalmente preta.  
  
 Depois de examinar um pixel incorretamente é colorido e descobrir que a saída do sombreador de pixel não é a cor do esperado, você pode usar o depurador HLSL para examinar o sombreador de pixels e descobrir o que aconteceu com a cor do objeto. Você pode usar o depurador HLSL para examinar o estado das variáveis HLSL durante a execução, percorrer o código HLSL e definir pontos de interrupção para ajudá-lo a diagnosticar o problema.  
  
#### <a name="to-examine-the-pixel-shader"></a>Para examinar o sombreador de pixels  
  
1.  Inicie a depuração do sombreador de pixel. No **histórico de Pixel gráfico** janela, sob o objeto do lado primitiva, **sombreador de Pixel**, escolha o **iniciar depuração** botão.  
  
2.  Nesse cenário, como o sombreador de pixel apenas transmite a cor do sombreador de vértice, é fácil observar o sombreador de pixels não é a origem do problema.  
  
3.  O ponteiro sobre `input.color`. Observe que seu valor é completamente opaco preto (0, 0, 0, 1).  
  
     ![O membro "cores" de "entrada" é preto. ] (media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")  
  
     Nesse cenário, o exame revela que a cor incorreta provavelmente é o resultado de um sombreador de vértice que não forneçam as informações de cor certa para o sombreador de pixel operar em.  
  
 Depois de determinar que o sombreador de vértice provavelmente não está fornecendo as informações adequadas para o sombreador de pixel, a próxima etapa é examinar o sombreador de vértice.  
  
#### <a name="to-examine-the-vertex-shader"></a>Para examinar o sombreador de vértice  
  
1.  Inicie a depuração do sombreador de vértice. No **histórico de Pixel gráfico** janela, sob o objeto do lado primitiva, **sombreador de vértice**, escolha o **iniciar depuração** botão.  
  
2.  Localize a estrutura de saída do sombreador de vértice — isso é a entrada para o sombreador de pixel. Nesse cenário, o nome dessa estrutura é `output`. Examine o código de sombreador de vértice e observe que o `color` membro o `output` estrutura foi definido explicitamente para preto completamente opaco, talvez como resultado de uma pessoa que está depurando esforços.  
  
3.  Confirme que o membro de cor nunca é copiado na estrutura de entrada. Porque o valor de `output.color` é definido como opaco totalmente preta antes o `output` estrutura é retornada, ele é uma boa ideia para certificar-se de que o valor de `output` não foi inicializado corretamente em uma linha anterior. Percorrer o código de sombreador de vértice até que a linha que define `output.color` para preto enquanto você observa que o valor de `output.color`. Observe que o valor de `output.color` não foi inicializado até que ele seja definido para preto. Isso confirma que a linha de código que define `output.color` para preto deve ser modificado, em vez de excluído.  
  
     ![O valor de "output.color" é preto. ] (media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")  
  
 Depois de determinar que a causa do problema de renderização é que o sombreador de vértice não fornece o valor de cor correta para o sombreador de pixel, você pode usar essas informações para corrigir o problema. Nesse cenário, você pode corrigi-lo alterando o código a seguir o sombreador de vértice  
  
```  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 para  
  
```hlsl  
output.color = input.color;  
```  
  
 Esse código passa apenas a cor de vértice por meio de vértices do objeto sem modificações — sombreadores de vértices mais complexos podem modificar a cor antes de passá-lo por meio. O código de sombreador de vértice corrigido deve ser semelhante a esta:  
  
 ![O código de sombreador de vértice corrigido. ] (media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")  
  
 Depois de corrigir o código, recriá-lo e executar o aplicativo novamente para descobrir se o problema de renderização é resolvido.  
  
 ![O objeto é processado com as cores corretas. ] (media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")