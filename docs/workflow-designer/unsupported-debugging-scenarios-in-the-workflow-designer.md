---
title: Sem suporte a cenários no Designer de fluxo de trabalho de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e2b250c44e6aa1fbbdf7c546c8e9bf15ffbbe008
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Cenários sem suporte de depuração no Designer de Fluxo de Trabalho
Designer de Fluxo de Trabalho em [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] adicionou muitos novos recursos, mas ainda há alguns cenários de depuração que não oferece suporte. Este documento detalha Designer de Fluxo de Trabalho sem suporte a depuração cenários.  
  
-   A execução não pode ser continuada após o código foi editado.  
  
-   A execução não pode ser continuada de um ponto arbitrário no fluxo de trabalho (definido em seguida).  
  
-   A execução não pode ser continuada até que o cursor seja alcançado (execução ao cursor).  
  
-   O designer de fluxo de trabalho não pode ser usado para criar fluxos de trabalho criados em código sem o uso de designer.  
  
-   Fluxos de trabalho criados em versões anteriores de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] não podem ser depurado no designer de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] .  
  
-   Os pontos de interrupção não podem ser definidos nos links entre atividades ou nós de <xref:System.Activities.Statements.Flowchart> .  
  
-   A área de transferência não estão disponíveis durante a depuração.  
  
-   Os pontos de interrupção não são mantidas quando as atividades são copiadas ou coladas.  
  
-   Os pontos de interrupção de fluxo de trabalho não podem ser definidos na janela de pilha de chamadas.  
  
-   Durante a criação de pontos de interrupção no designer, o **linha** e **caractere** configurações o **novo ponto de interrupção** caixa de diálogo não são usados.  
  
-   A janela ou o menu de atalho do ponto de interrupção não suportam as seguintes colunas ou opções para depuração de fluxo de trabalho:  
  
    -   Condição  
  
    -   Contagem de acertos  
  
    -   Quando atingido  
  
    -   Função  
  
    -   Dados  
  
    -   Processo  
  
    -   Vá para a desmontagem