---
title: 'DA0003: muitas amostras de kernel | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97e2e745b59a22110f6392e2cd6fec1aea0a667a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750227"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: muitas amostras de kernel
|||  
|-|-|  
|ID de regra|DA0003|  
|Categoria|Uso das ferramentas de criação de perfil|  
|Métodos de criação de perfil|Amostragem|  
|Mensagem|Há uma grande proporção de exemplos no Modo Kernel. Isso pode indicar um alto volume de atividade de E/S ou uma taxa alta de alternância de contexto. Considere criar um novo perfil para o aplicativo usando o Modo de Instrumentação.|  
|Tipo de regra|Informações|  
  
## <a name="cause"></a>Causa  
 Uma parte significativa dos exemplos de pilha de chamadas coletados para o aplicativo estavam sendo executados em modo kernel. Considere a criação de perfil para o aplicativo usando um método de criação de perfil diferente.  
  
## <a name="rule-description"></a>Descrição da regra  
 No Windows, o código pode ser executado no modo kernel ou no modo de usuário. (o modo kernel também é conhecido como modo privilegiado.) Somente o código de sistema de baixo nível, como um driver de dispositivo, é executado no modo kernel. Um aplicativo de modo de usuário pode fazer a transição para o modo kernel para executar operações de E/S, aguardar os primitivos de sincronização de thread ou de processo ou fazer chamadas do sistema.  
  
 A amostragem é a maneira mais eficaz ao criar perfis para aplicativos que passam a maior parte do tempo em modo de usuário. O número de amostras coletadas quando o aplicativo estava sendo executado no modo kernel pode indicar operações de E/S frequentes ou que esse alternâncias de contexto estão ocorrendo. Nenhuma dessas operações podem ser investigadas usando o método de amostragem. Caso muitas amostras do modo kernel forem usadas, os dados de amostragem podem não conter amostras suficientes de modo de usuário para serem estatisticamente significativos.  
  
## <a name="how-to-fix-violations"></a>Como corrigir violações  
 Considere criar um novo perfil para o aplicativo usando uma das opções a seguir:  
  
-   Crie perfis usando o método de instrumentação.  
  
-   Aumente a taxa de amostragem para coletar mais amostras no modo de usuário.