---
title: "Exibir um instantâneo do IntelliTrace etapa-back - Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc7ad92e708666baf1ab0429c041ca9b7d2e0f95
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="view-snapshots-using-intellitrace-step-back"></a>Instantâneos de modo de exibição usando o IntelliTrace etapa-back
Etapa-back do IntelliTrace automaticamente tira um instantâneo do seu aplicativo em cada ponto de interrupção e o depurador evento da etapa. Os instantâneos gravados permitem que você volte para os pontos de interrupção anteriores ou etapas e exibir o estado do aplicativo como ele era no passado. IntelliTrace back etapa pode economizar tempo quando você deseja ver o estado anterior do aplicativo, mas não deseja reiniciar a depuração ou recriar o estado do aplicativo desejado.

Etapa-back do IntelliTrace está disponível a partir 2017 de Enterprise do Visual Studio versão 15.5 e superior e requer a atualização de aniversário do Windows 10 ou superior. O recurso atualmente há suporte para depuração de ASP.NET, WinForms, WPF, aplicativos de console gerenciados e bibliotecas de classe gerenciada. Atualmente não há suporte para a depuração de aplicativos do ASP.NET Core, .NET Core ou UWP. 
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Habilitar o modo de eventos e os instantâneos do IntelliTrace 
Para habilitar o recurso, vá para **Ferramentas > Opções > IntelliTrace** configurações e selecione a opção **IntelliTrace eventos e instantâneos**. 

![Habilitar o modo de eventos do IntelliTrace e instantâneos](../debugger/media/intellitrace-enable-snapshots.png "ativar eventos do IntelliTrace e instantâneos de modo")

IntelliTrace tira um instantâneo do processo do aplicativo no depurador de cada evento de etapa e o ponto de interrupção. Esses eventos são registrados no **eventos** guia o **ferramentas de diagnóstico** janela, juntamente com outros eventos do IntelliTrace. Para abrir essa janela, escolha **depurar / Windows / Mostrar ferramentas de diagnóstico**.

Um ícone de câmera aparece ao lado de eventos para os quais os instantâneos estão disponíveis. 

![Guia eventos com instantâneos](../debugger/media/intellitrace-events-tab-with-snapshots.png "guia eventos com instantâneos em pontos de interrupção e etapas")

Por motivos de desempenho, instantâneos não são criados quando você entra muito rapidamente. Se nenhum ícone de câmera aparece ao lado da etapa, tente a revisão mais lentamente.

## <a name="navigate-and-view-snapshots"></a>Navegar e exibir instantâneos

Você pode navegar entre eventos usando o **com versões anteriores do etapa** e **Avançar** botões na barra de ferramentas Depurar. Esses botões navegar os eventos que aparecem no **eventos** guia o **janela ferramentas de diagnóstico**. Passo a passo para trás ou para frente a um evento automaticamente ativa a depuração histórica no evento selecionado.

![Etapa para trás e encaminhar botões](../debugger/media/intellitrace-step-back-icons-description.png "botões etapa com versões anteriores e Avançar")

Quando você voltar ou Avançar uma etapa, o Visual Studio entra em modo de depuração histórico. Nesse modo, o contexto do depurador alterna para a hora quando o evento selecionado foi gravado. O Visual Studio também move o ponteiro para a linha de código na janela de origem correspondente. 

Nessa exibição, você pode inspecionar os valores de **pilha de chamadas**, **locais**, **Autos**, e **inspecionar** windows. Você também pode passar sobre variáveis exibir DataTips e executar a avaliação da expressão de **imediato** janela. Os dados que você vê são desde o instantâneo do processo do aplicativo executado no momento.

Assim, por exemplo, se você tiver um ponto de interrupção e ampliada (**F10**), o **com versões anteriores do etapa** botão coloca o Visual Studio no modo de histórico na linha de código correspondente no ponto de interrupção. 

![Ativando o modo histórico em um evento com um instantâneo](../debugger/media/intellitrace-historical-mode-with-snapshot.png "ativando o modo histórico em um evento com um instantâneo")

Para retornar a execução, escolha **continuar (F5)** ou clique no **retornar à depuração dinâmica** link na barra de informações. 

Você também pode exibir um instantâneo do **eventos** guia. Selecione um evento com um instantâneo e clique em **Ativar depuração histórica**. Você também pode clicar no ícone de câmera para ativar a depuração histórica.

![Ativar depuração histórica em um evento](../debugger/media/intellitrace-activate-historical-debugging.png "ativar o recurso de depuração histórica em um evento")

Ao contrário de **definir próxima instrução** comando, exibindo um instantâneo não novamente seu código; ele fornece uma exibição estática do estado do aplicativo em um ponto no tempo em que ocorreu no passado.

![Visão geral do retorno do IntelliTrace etapa](../debugger/media/intellitrace-step-back-overview.png "visão geral do IntelliTrace etapa-back")

## <a name="next-steps"></a>Próximas etapas  
 Para saber como inspecionar variáveis no Visual Studio, consulte [tour pelos recursos do depurador](../debugger/debugger-feature-tour.md)  
 Para obter uma visão geral de depuração histórica, consulte [depuração histórica](../debugger/historical-debugging.md).  

## <a name="frequently-asked-questions"></a>Perguntas frequentes

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Como o IntelliTrace etapa-back é diferente do modo de somente de eventos do IntelliTrace?

IntelliTrace no modo somente eventos permitem que você ative a depuração histórica em pontos de interrupção e etapas do depurador. No entanto, o IntelliTrace captura apenas dados no **locais** e **Autos** windows se as janelas estão abertas, e captura apenas dados que são expandidos e no modo de exibição. No modo somente de eventos, você geralmente não tem uma visão completa de variáveis e objetos complexos. Além disso, expressão de avaliação e exibindo dados no **inspecionar** janela não tem suporte. 

No modo de eventos e os instantâneos do IntelliTrace captura todo o instantâneo do processo do aplicativo, incluindo objetos complexos. Em uma linha de código, você pode ver as mesmas informações como se você foi interrompido no ponto de interrupção (e não importa se você previamente expandidos as informações). Também há suporte para a avaliação da expressão ao exibir um instantâneo.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Qual é o impacto de desempenho desse recurso? 

O impacto no desempenho geral de revisão depende de seu aplicativo. A sobrecarga de tirar um instantâneo é em torno de 30 ms. Quando um instantâneo é criado, o processo do aplicativo estiver bifurcado e a cópia bifurcada é suspenso. Quando você exibir um instantâneo, o Visual Studio é anexar à cópia bifurcada do processo. Para cada instantâneo, o Visual Studio copia apenas a tabela de página e define páginas para copy-on-write. Se os objetos no heap alterar entre as etapas do depurador com instantâneos associados, a tabela a respectiva página, em seguida, é copiada, resultando em um custo mínimo de memória. Se o Visual Studio detectar que não há memória suficiente para criar um instantâneo, ele não tem um.
 
## <a name="known-issues"></a>Problemas conhecidos  
* Se você estiver usando o modo de eventos e os instantâneos do IntelliTrace em versões do Windows anterior ao Windows 10 outono criadores de atualização (RS3) e o destino de depuração de plataforma do aplicativo é definido para x86, IntelliTrace não instantâneos.

    Solução alternativa:
    * Instalar ou atualizar para o Windows 10 outono criadores de atualização (RS3). 
    * Como alternativa: 
        1. Instale o conjunto de ferramentas do VC++ 2015.3 v140 para o componente de área de trabalho (x86, x64) do Instalador do Visual Studio.
        2. Compile o aplicativo de destino.
        3. Na linha de comando, use a ferramenta editbin para definir o `Largeaddressaware` sinalizador para o executável de destino. Por exemplo, você pode usar esse comando (depois de atualizar o caminho): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
        4. Para iniciar a depuração, pressione **F5**. Agora, os instantâneos são realizados em pontos de interrupção e etapas do depurador.

        > [!Note]
        > O `Largeaddressaware` sinalizador deve ser definido de cada vez que o executável é recompilado com as alterações.

* Quando um instantâneo do processo do aplicativo é colocado em um aplicativo que usa um arquivo de mapeamento de memória persistente, o processo com o instantâneo mantém um bloqueio exclusivo no arquivo de mapeamento de memória (mesmo depois que o processo pai foi lançado seu bloqueio). Outros processos ainda são capazes de ler, mas não gravar no arquivo de mapeamento de memória.

    Solução alternativa:
    * Limpe todos os instantâneos de finalizar a sessão de depuração. 

* Ao salvar um arquivo com **Depurar > IntelliTrace > Salvar IntelliTrace sessão** no modo de eventos e instantâneos, os dados adicionais capturados de instantâneos não estão disponíveis no arquivo. itrace. Nos eventos de ponto de interrupção e etapa, você ver as mesmas informações como se tivesse salvou o arquivo no modo somente de eventos de IntelliTrace. 