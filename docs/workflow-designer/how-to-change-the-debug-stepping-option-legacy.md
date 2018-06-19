---
title: 'Designer de fluxo de trabalho - como: alterar a opção de Avançar de depuração (legados)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: 31047cedd4e8772b9ebab4ef238a8fe32bc07663
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971977"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Como: Altere a opção de avançar de depuração (o legados)

Este tópico descreve como alterar a opção para aplicativos do Windows Workflow Foundation (WF) no Designer de fluxo de trabalho herdado do Windows que têm ações simultâneas passo a passo de depuração. Use o Designer de fluxo de trabalho herdado quando você precisa direcionar o .NET Framework versão 3.5 ou o WinFX.

Quando você está depurando atividades herdadas com execução simultânea, tais como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções para depurar seu código.

Siga estas etapas para alterar a opção de avançar de depuração no seu projeto herdado de fluxo de trabalho.

## <a name="procedures"></a>Procedimentos

### <a name="to-change-the-debug-stepping-option"></a>Para alterar a opção de avançar de depuração

1.  Inicie o Visual Studio.

2.  Abrir um projeto de fluxo de trabalho herdado existente ou criar um novo projeto que emprega atividades simultâneas e que tem como destino o .NET Framework versão 3.5 ou o WinFX.

3.  Sobre o **fluxo de trabalho** menu no Designer de fluxo de trabalho herdados, aponte para **depurar**e, em seguida, aponte para **opções de revisão**.

4.  Selecione **instância** ou **ramificação**.

## <a name="see-also"></a>Consulte também

- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)
- [Opções de passo a passo em depuração (herdado)](../workflow-designer/debug-stepping-options-legacy.md)