---
title: Modos operacionais | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72ae5a36f9f0547635872f5c8ebe30f2f3c53d5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="operational-modes"></a>Modos operacionais
Há três modos nos quais o IDE pode operar, da seguinte maneira:  
  
-   [Modo de design](#vsconoperationalmodesanchor1)  
  
-   [Modo de execução](#vsconoperationalmodesanchor2)  
  
-   [Modo de interrupção](#vsconoperationalmodesanchor3)  
  
 Como o mecanismo de depuração personalizado (DE) faz a transição entre esses modos é uma decisão de implementação que exige que você esteja familiarizado com os mecanismos de transição. O DE pode ou não pode implementar diretamente esses modos. Esses modos estão realmente pacote modos de depuração que mudar com base na ação do usuário ou DE eventos. Por exemplo, a transição do modo de execução para o modo de interrupção é atraiu por um evento de interrupção a partir DE. A transição de interrupção para executar modo ou etapa é atraiu pelo usuário que está executando operações como etapa ou executar. Para obter mais informações sobre DE transições, consulte [controle de execução](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Modo de design  
 Modo de design é o estado nonrunning de depuração no Visual Studio, durante esse período, você pode definir recursos em seu aplicativo de depuração.  
  
 Depuração somente alguns recursos são usados durante o modo de design. Um desenvolvedor pode optar por definir pontos de interrupção ou criar expressões de inspeção. O DE nunca é carregado ou foi chamado enquanto o IDE estiver no modo de design. Interação com o DE acontece durante apenas modos de execução e quebra.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Modo de execução  
 Modo de execução ocorre quando um programa é executado em uma sessão de depuração no IDE. O aplicativo é executado até o encerramento, até que um ponto de interrupção é atingido, ou até que uma exceção será lançada. Quando o aplicativo é executado para encerramento, as transições DE no modo de design. Quando um ponto de interrupção é atingido ou uma exceção será lançada, o DE faz a transição para o modo de interrupção.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Modo de interrupção  
 Modo de interrupção ocorre quando a execução do programa de depuração é suspensa. Modo de interrupção oferece ao desenvolvedor um instantâneo do aplicativo no momento da interrupção e permite que o desenvolvedor analisar o estado do aplicativo e alterar como o aplicativo será executado. O desenvolvedor pode exibir e editar o código, examinar ou modificar dados, reinicie o aplicativo, terminar a execução ou continuar a execução do mesmo.  
  
 Modo de interrupção é inserido quando o DE envia um evento de parada síncrona. Eventos de interrupção síncrona, também chamados de eventos de interrupção, notificam o Gerenciador de sessão de depuração (SDM) e o IDE que o aplicativo que está sendo depurado parou de executar o código. O [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfaces são exemplos de eventos de interrupção.  
  
 Interrompendo eventos continuam por uma chamada para um dos métodos a seguir, que passa o depurador do modo de interrupção para executar ou etapa modo:  
  
-   [Executar](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Modo de etapa  
 Modo de etapa ocorre quando o programa de etapas para a próxima linha de código, ou em, acima ou fora de uma função. Uma etapa é executada chamando o método [etapa](../../extensibility/debugger/reference/idebugprocess3-step.md). Esse método requer `DWORD`s que especificam o [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) enumerações como parâmetros de entrada.  
  
 Quando o programa com êxito as etapas para a próxima linha de código ou em uma função, ou ele é executado até o cursor ou para um ponto de interrupção do conjunto, o DE mudará automaticamente para modo de interrupção.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução](../../extensibility/debugger/control-of-execution.md)