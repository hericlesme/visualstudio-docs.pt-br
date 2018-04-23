---
title: Escolhendo uma estratégia de implementação do mecanismo de depuração | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c3715bac00b25cd2080a1162c8e2ce8cb33e63a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Escolhendo uma estratégia de implementação do mecanismo de depuração
Use a arquitetura de tempo de execução para determinar sua estratégia de implementação do mecanismo (DE) de depuração. O mecanismo de depuração pode ser criado no processo para o programa a ser depurado, no processo para o Gerenciador de depuração de sessão do Visual Studio (SDM) ou fora de processo para ambos. As diretrizes a seguir devem ajudar a escolher entre esses três estratégias.  
  
## <a name="guidelines"></a>Diretrizes  
 Embora seja possível para o DE fora do processo do SDM tanto o programa a ser depurado, normalmente não há nenhum motivo para isso. Chamadas entre limites de processo são relativamente lentas.  
  
 Depurar mecanismos já são fornecidos para o ambiente de tempo de execução nativo do Win32 e para o ambiente de tempo de execução de linguagem comum. Se for necessário substituir DE para qualquer um desses ambientes, você deve criar o DE processo com o SDM.  
  
 Caso contrário, você pode escolher entre a criação DE em processo para o SDM ou em processo para o programa a ser depurado. É importante considerar se o avaliador de expressão de precisa ter acesso frequente para o armazenamento de símbolo de programa e se o repositório de símbolos pode ser carregado na memória para acesso rápido. Além disso, considere o seguinte:  
  
-   Se não houver muitas chamadas entre o avaliador de expressão e o armazenamento de símbolo, ou se o armazenamento de símbolo pode ser lido no espaço de memória do SDM, crie o DE em processo para o SDM. Você deve retornar o CLSID do mecanismo de depuração para o SDM quando ele se conecta ao seu programa. O SDM usa esse CLSID para criar uma instância no processo de.  
  
-   Se o DE deve chamar o programa para acessar o repositório de símbolos, crie o DE processo com o programa. Nesse caso, o programa cria a instância do DE.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)