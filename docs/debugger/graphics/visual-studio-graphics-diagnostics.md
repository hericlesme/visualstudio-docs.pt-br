---
title: Diagnóstico de gráficos do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e48abba7c137e40cef1e03f9d127adea08145e9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477726"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos do Visual Studio
O Visual Studio*diagnóstico de gráficos* é um conjunto de ferramentas para gravação e, em seguida, analisando problemas de desempenho e a renderização em aplicativos do Direct3D. Diagnóstico de gráficos pode ser usado em aplicativos que estão em execução localmente no seu PC com Windows, em um emulador de dispositivo do Windows ou em um computador remoto ou o dispositivo.  
  
 O fluxo de trabalho de diagnóstico de gráficos começa com a captura de um registro de como seu aplicativo usa Direct3D — ao vivo, ele é executado, para que seu comportamento pode ser analisado imediatamente, compartilhados ou salvas para mais tarde. Captura de sessões podem ser iniciadas e controlado manualmente do Visual Studio ou com a ferramenta de linha de comando captura **dxcap.exe**. Sessões de captura também podem ser iniciadas e controlado por meio de programação usando a APIs de captura de diagnóstico de gráficos.  
  
 Depois que uma sessão de captura foi registrada seu conteúdo pode ser reproduzido pelo Visual Studio *analisador de gráficos* a qualquer momento, recriando os quadros capturados usando os mesmos recursos exatos e comandos de processamento do aplicativo usado. Em seguida, usando as ferramentas fornecidas na janela de gráficos Analyer, qualquer um dos quadros capturados podem ser analisados em detalhes. Essas ferramentas podem ser usadas para examinar uma chamada de API do Direct3D, recursos, objeto de estado do pipeline, estágio do pipeline ou até mesmo o histórico completo de qualquer pixel em um quadro capturado. Usando essas ferramentas em conjunto, um problema de processamento pode ser explorado intuitivamente, começando em como ela aparece em um quadro capturado e Detalhar para sua causa raiz em ativos de gráficos, sombreadores ou código de origem do aplicativo.  
  
 Para diagnosticar problemas de desempenho, um quadro capturado pode ser analisado usando o *análise de quadros* ferramenta. Essa ferramenta explora otimizações de desempenho potencial automaticamente alterando o modo como o aplicativo usa Direct3D e benchmark todas as variações para você. No passado, você pode ter feito e por benchmark esses tipos de alterações manualmente apenas para localizar quais fez uma diferença de saída. Com a análise de quadros, basta fazer as alterações que você já souber será compensado.  
  
 Diagnóstico de gráficos ajuda seu aplicativo de Direct3D graficamente ricos pesquisar e executar o melhor desempenho.  
  
 Continuar a [visão geral](overview-of-visual-studio-graphics-diagnostics.md) para saber mais sobre o que o diagnóstico de gráficos do Visual Studio oferece.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral](overview-of-visual-studio-graphics-diagnostics.md)  
 Apresenta o fluxo de trabalho e as ferramentas de Diagnóstico de Gráficos.  
  
 [Introdução](getting-started-with-visual-studio-graphics-diagnostics.md)  
 Nesta seção, você aprenderá como instalar o diagnóstico de gráficos do Visual Studio e como começar a usar o diagnóstico de gráficos com seu aplicativo Direct3D.  
  
 [Capturando informações de gráficos](capturing-graphics-information.md)  
 Para usar o Diagnóstico de Gráficos para examinar um problema de renderização no aplicativo, primeiro registre informações sobre como o aplicativo usa o DirectX. Durante a sessão de gravação, como seu aplicativo é executada normalmente, você *capturar* (ou seja, selecione) os quadros que você está interessado. A captura contém informações detalhadas sobre como os quadros são renderizados. É possível salvar as informações capturadas como um documento de log de gráficos para examinar mais tarde ou compartilhar com outros membros da equipe.  
  
 [Uso de GPU](gpu-usage.md)  
 Para usar o diagnóstico de gráficos para criar o perfil de seu aplicativo, use a ferramenta uso da GPU. Uso de GPU pode ser usado em conjunto com outras ferramentas de criação de perfil, como uso de CPU para correlacionar a atividade da CPU e GPU que pode causar problemas de desempenho em seu aplicativo.  
  
 [Documento de log de gráficos](graphics-log-document.md)  
 Para iniciar o exame de um log gravado gráficos, você deve usar a janela de documento do Log de gráficos para selecionar um quadro capturado — ou até mesmo um pixel específico — para que você possa examinar detalhadamente o *eventos* (ou seja, o DirectX chamadas à API) que afetam a ele .  
  
 [Análise de quadros](graphics-frame-analysis.md)  
 Depois de selecionar um quadro, use a Análise de Quadros de Gráficos para examinar e ajustar seu desempenho de renderização.  
  
 [Lista de Eventos](graphics-event-list.md)  
 Depois de selecionar um quadro, você usar o **lista de eventos de gráfico** para examinar seus eventos para determinar se eles estão relacionados ao problema de renderização.  
  
 [Estado](graphics-state.md)  
 A janela de estado ajudará a entender o estado dos gráficos que está ativo no momento do evento atual.  
  
 [Estágios de Pipeline](graphics-pipeline-stages.md)  
 No **estágios de Pipeline gráficos** janela, examinar como o evento selecionado no momento é processado por cada estágio do pipeline de gráficos para que você possa identificar onde o problema de renderização aparece primeiro. Examinar os estágios do pipeline é especialmente útil quando um objeto não aparece devido a uma transformação incorreta ou quando um dos estágios produz uma saída que não corresponde ao que o próximo estágio espera.  
  
 [Pilha de Chamadas do Evento](graphics-event-call-stack.md)  
 Você usa o **pilha de chamadas do evento de gráficos** para examinar a pilha de chamadas do evento selecionado no momento, para que você possa navegar para o código de aplicativo que está relacionado ao problema de processamento.  
  
 [Histórico de Pixel](graphics-pixel-history.md)  
 Usando o **histórico de Pixel gráfico** janela para analisar como o pixel selecionado no momento é afetado pelos eventos que são influenciaram, você pode identificar o evento ou uma combinação de eventos que causam a determinados tipos de problemas de processamento. O histórico de pixel é especialmente útil quando um objeto é renderizado incorretamente porque a saída do sombreador de pixel está incorreta ou foi combinada incorretamente com o buffer de quadro, ou quando um objeto não aparece porque seus pixels foram descartados antes de atingir o buffer de quadro.  
  
 [Tabela de Objeto](graphics-object-table.md)  
 Você usa o **tabela de objetos gráficos** para examinar as propriedades e o conteúdo de objetos específicos do Direct3D e recursos que estão em vigor para o evento selecionado no momento. A tabela de objetos pode ajudar a determinar o contexto do dispositivo gráfico que está ativo durante um evento e examinar os conteúdos de recursos gráficos, como buffers constantes, buffers de vértices e texturas.  
  
 [Depurador HLSL](hlsl-shader-debugger.md)  
 Para examinar o código de sombreador para o evento selecionado no momento e gráficos de pipeline estágio comportamento, você deve usar o **depurador HLSL** para percorrer o código, examinar o conteúdo de variáveis e executar outras tarefas de depuração típicas. Também é possível usar o depurador HLSL para examinar o código do sombreador de computação, independente de os resultados serem processados mais pelo pipeline de gráficos ou apenas relidos pelo aplicativo.  
  
 [Ferramenta de captura de linha de comando](command-line-capture-tool.md)  
 Use a ferramenta de captura de linha de comando para capturar e reproduzir rapidamente informações de gráficos sem usar o Visual Studio ou captura programática. Em particular, você pode usar a ferramenta de captura de linha de comando para automação ou em um ambiente de teste.  
  
 [Exemplos](graphics-diagnostics-examples.md)  
 Vários exemplos demonstram como usar as ferramentas de Diagnóstico de Gráficos juntas para diagnosticar diferentes tipos de problemas de renderização.  
  
## <a name="related-sections"></a>Seções relacionadas  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Tour dos recursos do depurador](../debugging-in-visual-studio.md)|Apresenta a funcionalidade de depuração no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|  
|[Elementos gráficos do DirectX e jogos](http://go.microsoft.com/fwlink/?LinkId=256498)|Fornece artigos que discutem as tecnologias de gráficos do DirectX.|