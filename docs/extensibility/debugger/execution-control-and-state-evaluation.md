---
title: Controle de execução e o estado de avaliação | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d306ffe484605a081afa81afdcdcaa1a70339c84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098167"
---
# <a name="execution-control-and-state-evaluation"></a>Controle de execução e avaliação de estado
Depurando um aplicativo requer a implementação de recursos de controle, execução, como depuração em funções, parando em pontos de interrupção e continuando a execução. Depuração de bases de dados do Visual Studio seu controle de execução em eventos enviados entre componentes do depurador.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Controle do programa](../../extensibility/debugger/program-control.md)  
 Lista as seguintes rotinas que ocorrem no nível do programa: definir a próxima instrução, executando, passo a passo, continuar, suspender e retomar.  
  
 [Métodos relacionados ao ponto de interrupção](../../extensibility/debugger/breakpoint-related-methods.md)  
 Define o limite e pendentes tipos de pontos de interrupção que dá suporte ao Visual Studio.  
  
 [Avaliação de pilha de chamadas](../../extensibility/debugger/call-stack-evaluation.md)  
 Discute a implementação dos métodos que permitem a exibição de registros de ativação da pilha de chamadas durante o modo de interrupção.  
  
 [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explica como o mecanismo de depuração (DE), Gerenciador de expressões avaliação (EE) e a sessão de depuração estão envolvidos na análise e avaliação de uma expressão inserida em uma das janelas do IDE.  
  
 [Eventos de controle](../../extensibility/debugger/control-events.md)  
 Descreve a interface usada para enviar eventos durante a execução controlada do programa.