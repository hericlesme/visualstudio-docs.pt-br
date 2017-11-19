---
title: "Mecanismo de depuração de criar um personalizado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb5971bf86c6b97d38daaf86f3a093da196020da
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-custom-debug-engine"></a>Criando um mecanismo de depuração personalizado
Um mecanismo de depuração (DE) é um componente que permite a depuração de arquiteturas de tempo de execução específicas. Normalmente, há apenas uma implementação DE por ambiente de tempo de execução.  
  
> [!NOTE]
>  Embora haja implementações DE separadas para o Transact-SQL e JScript, VBScript e JScript compartilham DE um único.  
  
 A DE funciona com o sistema de operação ou interpretador para fornecer serviços depuração como avaliação de expressão, os pontos de interrupção e controle de execução. Esses serviços são implementados por meio DE interfaces e podem fazer com que o depurador para fazer a transição entre os modos operacionais diferentes. Para obter mais informações, consulte [modos operacionais](../../extensibility/debugger/operational-modes.md).  
  
 Criar um DE consiste das seguintes etapas:  
  
1.  Registrando um DE com o Visual Studio  
  
2.  Habilitar um programa a ser depurado  
  
3.  Avaliação de controle e estado de execução  
  
4.  Envio de eventos  
  
5.  Encerramento e desconectar  
  
## <a name="in-this-section"></a>Nesta seção  
 [Registrar um mecanismo de depuração personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explica as etapas necessárias para registrar um mecanismo de depuração com o Visual Studio para que ele possa ser usado.  
  
 [Habilitar um programa para depuração](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explica antes de sua ir pode depurar um programa, você deve primeiro iniciar o DE ou anexá-lo para um programa existente.  
  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Descreve por que estiver depurando um aplicativo requer a implementação de recursos de controle de execução.  
  
 [Enviar eventos](../../extensibility/debugger/sending-events.md)  
 Descreve a comunicação entre o depurador e DE como um modelo de evento com base em DCOM.  
  
 [Encerramento e desanexação](../../extensibility/debugger/termination-and-detaching.md)  
 Explica como obter um encerramento normal, o que significa que não há pontos de interrupção, exceções, erros de tempo de execução ou loops infinitos no aplicativo a ser depurado.  
  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta a ordem dos eventos que ocorrem em uma sessão de depuração de chamada.  
  
 [Como depurar um mecanismo de depuração personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explica como depurar um DE personalizado.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)