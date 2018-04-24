---
title: Capturando informações de gráficos | Microsoft Docs
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e00dd4d0fae184f092efabb5df4a4f27e76a653a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="capturing-graphics-information"></a>Capturando informações de gráficos
Capture informações de gráficos do seu aplicativo Direct3D para que você possa usar o analisador de gráficos do Visual Studio para diagnosticar problemas de desempenho e problemas de processamento.  
  
## <a name="capturing-graphics-information"></a>Capturando informações de gráficos  
 A captura de informações de gráficos é um processo de duas etapas. Primeiramente, você executa o aplicativo em Diagnóstico de Gráficos e depois especifica um ou mais quadros dos quais serão capturadas informações detalhadas.  
  
### <a name="to-run-your-app-under-graphics-diagnostics"></a>Para executar o aplicativo em Diagnóstico de Gráficos  
  
-   Na barra de menus, escolha **depurar**, **gráficos**, **iniciar depuração de gráficos**. (Teclado: pressione Alt+F5)  
  
-   Sobre o **gráficos** barra de ferramentas, escolha o **iniciar depuração de gráficos** botão.  
  
 Enquanto um aplicativo estiver sendo executado no Diagnóstico de Gráficos, determinados tipos de informação de gráfico são capturados o tempo todo; isso inclui a configuração do dispositivo, a criação da cadeia de troca, a criação de recursos e objetos gráficos, bem como outros eventos importantes que afetam mais de um quadro. Ao mesmo tempo, você pode capturar informações detalhadas sobre quadros específicos; isso inclui chamadas de desenho e distribuições de sombreadores de cálculo, juntamente com os recursos e objetos Direct3D que oferecem suporte a eles.  
  
### <a name="to-capture-a-frame"></a>Para capturar um quadro  
  
-   No Visual Studio, no **gráficos** barra de ferramentas, clique no **capturar quadro** botão ![gráficos capturar o ícone do botão](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
-   No teclado, pressione a tecla Print Screen.
  
    > [!NOTE]
    >  Enquanto um aplicativo está em execução em **diagnóstico de gráficos**, a chave Print Screen só pode ser usada para capturar um quadro de informações de gráficos; ele não executa sua função regular. Isso permanece em vigor até que você pare de capturar informações de gráficos, geralmente interrompendo a depuração ou saindo do aplicativo normalmente, mesmo que outro aplicativo esteja no foco.  
  
-   Na interface de captura do Visual Studio, escolher o **capturar quadro** botão localizado abaixo do **sessão de diagnóstico** linha do tempo, ou escolha a grande **capturar quadro** botão localizada abaixo do **quadros por segundo** -Raia e à direita de todos os quadros capturados anteriormente. Ambos os botões estão realçados na imagem abaixo.  
  
     ![Capture quadros usando a ferramenta uso da GPU.](media/pix_gpu_usage_tool_capture_frame.png)  
  
     Quando você estiver pronto para examinar os quadros já capturados, inicie o **analisador de gráficos do Visual Studio** seguindo o **quadro...**  link acima as miniaturas de imagem, ou clicando duas vezes na miniatura.  
  
 Somente os quadros inteiros podem ser capturados, quando você inicia uma captura, é realmente as informações de gráficos de próximo quadro que é registrado. A gravação começa logo depois que o quadro no qual você iniciou a captura é apresentado e termina quando o quadro capturado é apresentado. É possível capturar quantos quadros você desejar enquanto o aplicativo estiver em execução no Diagnóstico de Gráficos. Se você não capturar nenhum quadro, o log de elementos gráficos será descartado.  
  
 Durante a captura de quadros, o Visual Studio exibe a janela de sessão (diagsession) de diagnóstico. Se você fecha esta janela, interrompa a depuração ou fecha o aplicativo, você não pode capturar mais quadros para esse log. Para capturar informações de gráficos mais, você precisa executar o aplicativo com o diagnóstico de gráficos novamente para iniciar uma nova sessão de diagnóstico.  
  
### <a name="graphics-diagnostics-capture-options"></a>Opções de captura de diagnóstico de gráficos  
 Você pode configurar a captura para coletar as pilhas de chamada para todos os eventos de gráficos ou um subconjunto limitado, desabilitar a captura HUD e ativar ou desativar o modo de compatibilidade de captura.  
  
#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Para configurar as opções de captura do diagnóstico de gráficos  
  
1.  Na barra de menus, escolha Ferramentas, Opções. A caixa de diálogo Opções é exibida.  
  
2.  Na lista de categorias de opções à esquerda, escolha o diagnóstico de gráficos, e configurar as opções de diagnóstico de gráficos que você deseja.  
  
     **Coletar pilhas de chamadas durante a captura (deixa a captura mais lenta)**  
     Marque esta caixa para coletar as pilhas de chamadas. Por padrão, as pilhas de chamadas não são coletadas. Para capturar as pilhas de chamadas, verifique se o **chamada coletar pilhas durante a captura (deixa a captura mais lenta** caixa de seleção é definida para habilitar a coleta e, em seguida, definir o **para marcadores de desenho, expedição, presente e desempenho**opção (padrão) para coletar somente as mais importantes pilhas de chamadas, ou o **para tudo** opção para coletar todas as pilhas de chamadas. Para interromper a coleta de pilhas de chamadas mais tarde, desmarque o **chamada coletar pilhas durante a captura (deixa a captura mais lenta** caixa de seleção.  
  
     **Desabilitar o jogo HUD durante a captura**  
     Marque essa caixa para desabilitar a sobreposição HUD que um aplicativo executando em diagnóstico de gráficos geralmente exibe. Desmarque essa opção para exibir a sobreposição HUD.  
  
     **Capturar em modo de compatibilidade**  
     Marque esta caixa para capturar informações de gráficos no modo de compatibilidade. A captura no modo de compatibilidade é o padrão. No modo de compatibilidade, o Direct3D não irá relatar que a GPU é compatível com todos os recursos adicionais além daqueles definidos no nível de recurso base. Isso evita que o aplicativo sendo capturado use extensões específicas de hardware da GPU em que é capturado e garante que o log de elementos gráficos possa ser executado usando qualquer GPU compatível com o mesmo nível de recurso ou superior. Desmarque essa caixa para desabilitar o modo de compatibilidade. Os logs capturados com o modo de compatibilidade desabilitado não conseguirão reproduzir em nenhuma GPU que não seja compatível com os mesmos recursos adicionais que foram usados pelo aplicativo durante a captura.  
  
     **Parar captura se forem encontrados erros camadas SDK**  
     Marque esta caixa para interromper a captura imediatamente se forem encontrados erros.  
  
## <a name="capturing-graphics-information-remotely"></a>Capturando informações de gráficos remotamente  
 As informações de gráficos podem ser capturadas de um aplicativo que está em execução no computador local, de um dispositivo ou computador remoto. A captura remota tem suporte em computadores com [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] e dispositivos com [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)]. Para capturar informações de gráficos de um aplicativo que está em execução remotamente, configure seu projeto para depuração remota e execute o aplicativo em Diagnóstico de Gráficos, como descrito anteriormente. O aplicativo é executado no computador remoto e as informações de gráficos capturadas são gravadas no computador de desenvolvimento.  
  
 Como você configura o projeto para depuração remota depende do tipo de aplicativo que está sendo desenvolvido e da linguagem de programação que está sendo usada. Para obter informações sobre como configurar a depuração remota para um aplicativo UWP, consulte [UWP executar aplicativos em um computador remoto](../run-windows-store-apps-on-a-remote-machine.md). Para obter informações sobre como configurar a depuração remota para um aplicativo de área de trabalho do Windows, consulte [depuração remota](../remote-debugging.md).  
  
 Posteriormente, você pode usar um dispositivo ou computador remoto para reproduzir informações de gráficos, independentemente de onde as informações foram capturadas. Para obter mais informações, consulte [como: alterar a máquina de reprodução de diagnóstico de gráficos](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Captura de informações de elementos gráficos da linha de comando  
 Informações de gráficos poderão ser capturadas em um aplicativo usando uma ferramenta de linha de comando. Essa ferramenta, DXCap.exe, pode capturar e reproduzir rapidamente informações de gráficos sem usar o Visual Studio ou a captura programática. Em específico, você pode usar o DXCap.exe para automação ou em um ambiente de teste. Para obter mais informações sobre DXCap.exe, consulte [a ferramenta de captura de linha de comando](command-line-capture-tool.md)  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: capturando informações de gráficos](walkthrough-capturing-graphics-information.md)