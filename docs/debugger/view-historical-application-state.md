---
title: Exibir o estado anterior do aplicativo usando o IntelliTrace
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85b34fd85e8449949bb1e96efc1dd79aacbc1bd9
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48243946"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>Inspecionar estados anteriores do aplicativo usando o retrocesso do IntelliTrace no Visual Studio

Retrocesso do IntelliTrace automaticamente tira um instantâneo do seu aplicativo em cada ponto de interrupção e o depurador do evento de etapa. Os instantâneos registrados permitem retornar aos pontos de interrupção ou às etapas anteriores e exibir o estado do aplicativo como ele era no passado. O retrocesso do IntelliTrace poderá poupar seu tempo quando você desejar ver o estado do aplicativo anterior, mas não desejar reiniciar a depuração nem recriar o estado do aplicativo desejado.

Retrocesso do IntelliTrace está disponível a partir do Visual Studio Enterprise 2017 versão 15.5 e posterior, e ela requer a atualização de aniversário do Windows 10 ou superior. O recurso no momento, há suporte para depuração de ASP.NET, WinForms, WPF, aplicativos de console gerenciados e bibliotecas de classes gerenciadas. Começando com o Visual Studio 2017 Enterprise versão 15.7, o recurso também há suporte para ASP.NET Core e .NET Core. Começando com o Visual Studio 2017 Enterprise versão 15,9 Preview 2, o recurso também há suporte para aplicativos nativos, visando o Windows. Atualmente, não há suporte para a depuração de aplicativos UWP.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Habilitar instantâneos e eventos do Intellitrace
> * Navegar usando os comandos de retrocesso e avanço de etapa de eventos
> * Exibir instantâneos de evento
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Habilitar o modo de eventos e instantâneos do IntelliTrace 

1. Abra seu projeto no Visual Studio Enterprise.

1. Abra **ferramentas** > **opções** > **IntelliTrace** configurações e selecione a opção **IntelliTrace eventos e instantâneos** . 

    A partir do Visual Studio 2017 Enterprise versão 15,9 Preview 2, essa opção é **instantâneos do IntelliTrace (gerenciados e nativos)**. 

    ![Habilitar o modo de eventos do IntelliTrace e Snapshots](../debugger/media/intellitrace-enable-snapshots.png "ativar eventos do IntelliTrace e instantâneos de modo")

1. Se você deseja configurar as opções de visualização instantâneos em exceções, escolha **IntelliTrace** > **avançado** do **opções** caixa de diálogo.

    Essas opções estão disponíveis a partir do Visual Studio 2017 Enterprise versão 15.7.

    ![Configurar o comportamento para instantâneos em exceções](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Quando você habilita a eventos e instantâneos, tirar instantâneos em exceções também é habilitada por padrão. Você pode desabilitar os instantâneos em exceções, desmarcando **coletar instantâneos em eventos de exceção**. Quando esse recurso está habilitado, os instantâneos são executados para exceções sem tratamento. Para exceções controladas, os instantâneos são executados somente se a exceção é lançada e se não for um relançar uma exceção gerada anteriormente. Você pode definir um número máximo de instantâneos em exceções, selecionando um valor na lista suspensa. Aplica o máximo de cada vez que seu aplicativo entra em modo de interrupção (por exemplo, quando o aplicativo atinge um ponto de interrupção).

    > [!NOTE]
    > Instantâneos são executados somente para eventos de exceção de que o IntelliTrace registra. Para código gerenciado, você pode especificar quais eventos IntelliTrace registra, selecionando **ferramentas** > **opções** > **eventos do IntelliTrace**.

1. Em seu projeto, defina um ou mais pontos de interrupção e iniciar a depuração (pressione **F5**), ou iniciar a depuração, percorrendo seu código (**F10** ou **F11**).

    IntelliTrace tira um instantâneo do processo do aplicativo em cada etapa do depurador, o evento de ponto de interrupção e o evento de exceção sem tratamento. Esses eventos são registrados na **eventos** guia o **ferramentas de diagnóstico** janela, bem como outros eventos do IntelliTrace. Para abrir essa janela, escolha **Debug** > **Windows** > **Mostrar ferramentas de diagnóstico**.

    Um ícone de câmera aparece ao lado de eventos para o qual os instantâneos estão disponíveis. 

    ![Guia de eventos com instantâneos](../debugger/media/intellitrace-events-tab-with-snapshots.png "guia eventos com instantâneos de pontos de interrupção e etapas")

    Por motivos de desempenho, os instantâneos não são executados quando você entra muito rapidamente. Se nenhum ícone de câmera aparece ao lado da etapa, tente depurar mais lentamente.

## <a name="navigate-and-view-snapshots"></a>Navegar e exibir instantâneos

1. Navegar entre os eventos usando o **voltar (Alt + [)** e **Avançar uma etapa (Alt +])** botões na barra de ferramentas Depurar.

    Esses botões navegam pelos eventos que aparecem na **eventos** guia o **janela ferramentas de diagnóstico**. Voltar ou Avançar automaticamente a um evento ativa [depuração histórica](../debugger/historical-debugging.md) no evento selecionado.

    ![Retroceda e avance botões](../debugger/media/intellitrace-step-back-icons-description.png "botões Voltar e Avançar uma etapa")

    Quando você voltar ou Avançar uma etapa, o Visual Studio entra em modo de depuração histórica. Nesse modo, o contexto do depurador alterna para a hora quando o evento selecionado foi registrado. Visual Studio também move o ponteiro para a linha de código na janela de origem correspondente. 

    Nessa exibição, você pode inspecionar os valores a **pilha de chamadas**, **Locals**, **Autos**, e **inspeção** windows. Você também pode passar sobre variáveis exibir DataTips e executar a avaliação da expressão de **imediato** janela. Os dados que você vê são do instantâneo do processo do aplicativo executado no momento.

    Portanto, por exemplo, se você tiver um ponto de interrupção e ampliada (**F10**), o **voltar** botão coloca o Visual Studio no modo histórica na linha de código correspondente ao ponto de interrupção. 

    ![Ativando o modo histórico em um evento com um instantâneo](../debugger/media/intellitrace-historical-mode-with-snapshot.png "ativando o modo histórico em um evento com um instantâneo")

2. Para retornar à execução ao vivo, escolha **continuar (F5)** ou clique no **retornar à depuração dinâmica** link na barra de informações. 

3. Você também pode exibir um instantâneo a partir do **eventos** guia. Para fazer isso, selecione um evento com um instantâneo e clique em **Ativar depuração histórica**.

    ![Ativar o histórico de depuração em um evento](../debugger/media/intellitrace-activate-historical-debugging.png "ativar histórico de depuração em um evento")

    Ao contrário do **definir próxima instrução** comando, exibindo um instantâneo não executará novamente seu código; ele fornece uma exibição estática do estado do aplicativo em um ponto no tempo em que ocorreu no passado.

    ![Visão geral do retrocesso do IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "visão geral de retrocesso do IntelliTrace")

    Para saber mais sobre como inspecionar variáveis no Visual Studio, consulte [tour pelos recursos do depurador](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Perguntas frequentes

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Como o retrocesso do IntelliTrace é diferente do modo de somente de eventos do IntelliTrace?

IntelliTrace no modo somente de eventos permitem que você ativar depuração histórica em pontos de interrupção e etapas do depurador. No entanto, o IntelliTrace captura dados em somente o **Locals** e **Autos** windows, se as janelas estão abertas, e captura apenas os dados que são expandidos e no modo de exibição. No modo somente de eventos, você geralmente não tem uma visão completa das variáveis e objetos complexos. Além disso, avaliação e a exibição de dados de expressão na **inspeção** não há suporte para a janela. 

No modo de eventos e instantâneos do IntelliTrace captura todo o instantâneo do processo do aplicativo, incluindo objetos complexos. Em uma linha de código, você pode ver as mesmas informações como se você foi interrompido no ponto de interrupção (e não importa se você expandiu previamente as informações). Também há suporte para a avaliação da expressão ao exibir um instantâneo.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>O que é o impacto de desempenho desse recurso? 

O impacto no desempenho geral do passo a passo depende de seu aplicativo. A sobrecarga de tirar um instantâneo é cerca de 30 ms. Quando um instantâneo é tirado, o processo do aplicativo é bifurcado e a cópia bifurcada é suspenso. Quando você exibir um instantâneo, o Visual Studio está relacionada a anexar à cópia bifurcada do processo. Para cada instantâneo, o Visual Studio copia apenas a tabela de página e define páginas para copy-on-write. Se alterar objetos no heap entre as etapas do depurador com instantâneos associados, a tabela a respectiva página então é copiada, resultando em um custo mínimo de memória. Se o Visual Studio detectar que não há memória suficiente para criar um instantâneo, ela não leva um.
 
## <a name="known-issues"></a>Problemas Conhecidos  
* Se você estiver usando o modo de eventos e instantâneos do IntelliTrace em versões do Windows anteriores ao Windows 10 Fall Creators Update (RS3) e se o destino da plataforma de depuração do aplicativo for definido como x86, o IntelliTrace não tirar instantâneos.

    Soluções alternativas:
    * Se você estiver em atualização de aniversário do Windows 10 (RS1) e abaixo da versão 10.0.14393.2273, [instalar KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720). 
    * Se você estiver no Windows 10 Creators Update (RS2) e abaixo da versão 10.0.15063.1112, [instalar KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
    * Instalar ou atualizar para o Windows 10 Fall Creators Update (RS3). 
    * Como alternativa: 
        1. Instale o conjunto de ferramentas do VC++ 2015.3 v140 para o componente de área de trabalho (x86, x64) do Instalador do Visual Studio.
        2. Compile o aplicativo de destino.
        3. Na linha de comando, use a ferramenta editbin para definir o `Largeaddressaware` sinalizador para o executável de destino. Por exemplo, você pode usar esse comando (depois de atualizar o caminho): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
        4. Para iniciar a depuração, pressione **F5**. Agora, os instantâneos são executados com os pontos de interrupção e etapas do depurador.

        > [!Note]
        > O `Largeaddressaware` sinalizador deve ser definido sempre que o executável é recompilado com as alterações.

* Quando um instantâneo do processo do aplicativo for criado em um aplicativo que usa um arquivo persistente mapeado na memória, o processo com o instantâneo mantém um bloqueio exclusivo no arquivo mapeado em memória (até mesmo depois que o processo pai lançou seu bloqueio). Outros processos ainda são capazes de ler, mas não gravar no arquivo mapeado em memória.

    Solução alternativa:
    * Desmarque todos os instantâneos encerrando a sessão de depuração. 

* Ao depurar um aplicativo cujo processo tem um grande número de regiões de memória exclusivo, como um aplicativo que carrega um grande número de DLLs, passo a passo de desempenho com instantâneos habilitados pode ser afetada. Esse problema será corrigido em uma versão futura do Windows. Se você estiver enfrentando esse problema, contate-nos em stepback@microsoft.com. 

* Ao salvar um arquivo com **Depurar > IntelliTrace > sessão do IntelliTrace salvar** no modo de eventos e instantâneos, os dados adicionais capturados de instantâneos não estão disponíveis no arquivo. itrace. Eventos de ponto de interrupção e etapa, você ver as mesmas informações como se você salvou o arquivo no modo somente de eventos do IntelliTrace. 

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como usar o retrocesso do IntelliTrace. Você talvez queira saber mais sobre outros recursos do IntelliTrace.

> [!div class="nextstepaction"]
> [Recursos do IntelliTrace](../debugger/intellitrace-features.md)
