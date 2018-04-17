---
title: 'Como: alterar a opção de Avançar de depuração (legados) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aedb8e738dc2e6ca2b066dd9a2cd42e332bbd8be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Como: Altere a opção de avançar de depuração (o legados)
Este tópico descreve como alterar a opção de revisão de depuração para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicativos no Designer de fluxo de trabalho herdado do Windows que têm ações simultâneas. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Quando você está depurando atividades herdadas com execução simultânea, tais como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções para depurar seu código.

 Siga estas etapas para alterar a opção de avançar de depuração no seu projeto herdado de fluxo de trabalho.

## <a name="procedures"></a>Procedimentos

#### <a name="to-change-the-debug-stepping-option"></a>Para alterar a opção de avançar de depuração

1.  Inicie o Visual Studio.

2.  Abrir um projeto existente herdado de fluxo de trabalho ou criar um novo projeto que empreguem atividades simultâneas e que tem como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

3.  Sobre o **fluxo de trabalho** menu herdado [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], aponte para **depurar**e, em seguida, aponte para **opções de revisão**.

4.  Selecione **instância** ou **ramificação**.

## <a name="see-also"></a>Consulte também

- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)
- [Opções de passo a passo em depuração (herdado)](../workflow-designer/debug-stepping-options-legacy.md)