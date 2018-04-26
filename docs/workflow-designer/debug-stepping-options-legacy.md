---
title: Designer de fluxo de trabalho - opções de revisão de depuração (legados)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="debug-stepping-options-legacy"></a>Opções de avançar de depuração (legados)

Este tópico descreve como depurar aplicativos do Windows Workflow Foundation (WF) que têm atividades simultâneas no Designer de fluxo de trabalho herdado do Windows. Use o Designer de fluxo de trabalho herdado quando você precisa direcionar o .NET Framework versão 3.5 ou o WinFX.

Quando você está depurando atividades herdadas com execução simultânea, tais como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções a seguir para depurar seu código .

-   **Avançar de ramificação.** Este modo de depuração permite que você percorrer e depurar uma ramificação específica de uma atividade composta, como o **ParallelActivity** ou **ConditionalActivityGroup** atividade. Quando você usa esta opção depuração, você não irá notar que uma alteração no controle ocorre devido à execução simultânea de outras atividades no fluxo de trabalho. As etapas do depurador somente com as atividades na ramificação atualmente selecionado quando outras atividades no fluxo de trabalho podem executar simultaneamente. Por exemplo, por padrão, a ramificação mais à esquerda em um **ParallelActivity** atividade e a primeira atividade filho de um **ConditionedActivityGroup** atividade são usados para depuração. Se o usuário estiver interessado em depurar qualquer outra atividade de ramificação ou filhos, um ponto de interrupção explícito deve ser colocado na atividade de ramificação ou filho. Depuração continua naquela ramificação quando o ponto de interrupção é disparado.

-   **Avançar de instância.** Este modo de avançar permite que você entrar completamente e depurar executar simultaneamente atividades no fluxo de trabalho. Com essa opção, você observará que uma alteração no controle ocorre ao executar simultaneamente atividades é executado dentro de fluxo de trabalho.

Por padrão, a opção de avançar da ramificação é selecionada, e os usuários podem alternar entre as duas opções para depurar um fluxo de trabalho herdado.

Você deve selecionar a opção de avançar da instância ao depurar fluxos de trabalho herdados do computador de estado.

## <a name="see-also"></a>Consulte também

- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)
- [Como alterar a opção de executar a depuração em etapas (herdado)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)