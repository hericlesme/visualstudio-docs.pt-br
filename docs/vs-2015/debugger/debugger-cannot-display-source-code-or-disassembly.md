---
title: Depurador não pode exibir código-fonte ou desmontagem | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd21a38123894e7254bf4af6629528f8af4bf52d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467843"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>O depurador não pode exibir o código-fonte ou a desmontagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [depurador não é possível exibir código-fonte código ou a desmontagem](https://docs.microsoft.com/visualstudio/debugger/debugger-cannot-display-source-code-or-disassembly).  
  
Este erro é:  
  
 O depurador não pode exibir o código-fonte ou a desmontagem do local atual no qual a execução foi interrompida.  
  
 Essa mensagem de erro pode ocorrer por várias razões:  
  
-   Você pode ter atingido um ponto de interrupção em um local para o qual não há o código-fonte, ao depurar uma linguagem que não oferece suporte a desmontagem. Abra o **pontos de interrupção** , localize o ponto de interrupção e excluí-lo.  
  
-   Se você estiver depurando scripts, você pode ter atingido um ponto de interrupção enquanto não havia nenhum thread em seu programa. Escolher **etapa** ou **continuar** do **depurar** menu para continuar a depuração.  
  
-   Os critérios de segurança podem ter impedido que o depurador lesse a pilha, o thread, o registro e outras informações de contexto do programa que você está depurando. É mais provável que isso ocorra se você estiver depurando um aplicativo Web e não tiver a permissão correta para acessar o diretório virtual. Defina a segurança do diretório virtual como Anônima e tente novamente.  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)



