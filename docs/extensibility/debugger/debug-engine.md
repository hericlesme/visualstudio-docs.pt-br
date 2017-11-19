---
title: "Mecanismo de depuração | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2db510e81231f7802d686b21a977c271a66c5d79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debug-engine"></a>Mecanismo de depuração
Um mecanismo de depuração (DE) funciona com o sistema operacional ou interpretador para fornecer serviços de depuração, como avaliação de expressão, os pontos de interrupção e controle de execução. O DE é responsável por monitorar o estado de um programa que está sendo depurado. Para fazer isso, o DE usa qualquer métodos estão disponíveis para ele no tempo de execução com suporte, se da CPU ou APIs fornecidos pelo tempo de execução.  
  
 Por exemplo, o common language runtime (CLR) fornece mecanismos para monitorar um programa em execução por meio de interfaces ICorDebugXXX. A DE que suporta o CLR usa as interfaces de ICorDebugXXX apropriadas para manter o controle de um programa de código gerenciado que está sendo depurado. Ele se comunica as alterações de estado para o Gerenciador de depuração de sessão (SDM), que encaminha essas informações para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  Um mecanismo de depuração tem como alvo um tempo de execução específico, ou seja, o sistema no qual o programa que está sendo depurado é executado. O CLR é o tempo de execução de código gerenciado e o tempo de execução do Win32 é para aplicativos nativos do Windows. Se o idioma que você criar pode direcionar um desses dois tempos de execução [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] já fornece os mecanismos de depuração necessárias. Tudo o que você precisa implementar é um avaliador de expressão.  
  
## <a name="debug-engine-operation"></a>Operação do mecanismo de depuração  
 Os serviços de monitoramentos são implementados por meio DE interfaces e podem fazer com que o pacote de depuração para fazer a transição entre os modos operacionais diferentes. Para obter mais informações, consulte [modos operacionais](../../extensibility/debugger/operational-modes.md). Normalmente, há apenas uma implementação DE por ambiente de tempo de execução.  
  
> [!NOTE]
>  Embora haja em implementações DE separadas para o Transact-SQL e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] compartilham um único DE.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Habilita depuração depuração mecanismos para executar uma das seguintes maneiras: no mesmo processo que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de shell ou no mesmo processo que o programa de destino que está sendo depurado. O segundo formulário normalmente ocorre quando o processo que está sendo depurado é realmente um script em execução sob um intérprete e o mecanismo de depuração deve ter conhecimento profundo do intérprete para monitorar o script. Observe que, nesse caso, o interpretador é realmente um tempo de execução; mecanismos de depuração são para implementações de tempo de execução específica. Além disso, a implementação de um único DE pode ser dividida em limites de processo e de máquina (por exemplo, a depuração remota).  
  
 O DE expõe o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaces de depuração. Toda a comunicação está usando COM. Se o DE é carregado no processo, fora do processo ou em outro computador, ele não afeta a comunicação de componente.  
  
 O DE funciona com um componente do avaliador de expressão para habilitar o DE para esse tempo de execução específico entender a sintaxe das expressões. O DE também funciona com um componente do manipulador de símbolo para acessar as informações de depuração simbólicas geradas pelo compilador de linguagem. Para obter mais informações, consulte [avaliador de expressão](../../extensibility/debugger/expression-evaluator.md) e [provedor símbolo](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)   
 [Avaliador de expressão](../../extensibility/debugger/expression-evaluator.md)   
 [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md)