---
title: Escolhendo uma estratégia de implementação do mecanismo de depuração | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a9e449fddad18c3ff0e95786ab852745407e6a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463509"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Escolhendo uma estratégia de implementação de mecanismo de depuração
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [escolhendo uma estratégia de implementação do mecanismo de depuração](https://docs.microsoft.com/visualstudio/extensibility/debugger/choosing-a-debug-engine-implementation-strategy).  
  
Use a arquitetura de tempo de execução para determinar sua estratégia de implementação de (DES) do mecanismo de depuração. O mecanismo de depuração pode ser criado no processo para o programa a ser depurado, no processo no Gerenciador de depuração de sessão do Visual Studio (SDM) ou out-of-process para ambos. As diretrizes a seguir devem ajudar a escolher entre essas três estratégias.  
  
## <a name="guidelines"></a>Diretrizes  
 Embora seja possível para o DE ser out-of-process para o SDM e o programa a ser depurado, normalmente há nenhum motivo para fazer isso. Chamadas entre limites de processo são relativamente lentas.  
  
 Depurar mecanismos já são fornecidos para o ambiente de tempo de execução nativo do Win32 e para o ambiente do common language runtime. Se for necessário substituir o DE para qualquer um desses ambientes, você deve criar o DE processo com o SDM.  
  
 Caso contrário, você pode escolher entre a criação DE em processo para o SDM ou em processo para o programa a ser depurado. É importante considerar se o avaliador de expressão de precisa de acesso frequente para o repositório de símbolos do programa e se o repositório de símbolos pode ser carregado na memória para acesso rápido. Além disso, considere o seguinte:  
  
-   Se não houver muitas chamadas entre o avaliador de expressão e o repositório de símbolos, ou se o repositório de símbolos pode ser lidos no espaço de memória do SDM, crie o DE em processo para o SDM. Você deve retornar o CLSID do mecanismo de depuração para o SDM quando ele se conecta ao seu programa. O SDM usa este CLSID para criar uma instância no processo de.  
  
-   Se o DE deve chamar o programa para acessar o repositório de símbolos, crie o DE processo com o programa. Nesse caso, o programa cria a instância do DE.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

