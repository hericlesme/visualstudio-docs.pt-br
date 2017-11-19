---
title: "Erro: O computador remoto não aparecem em uma caixa de diálogo conexões remotas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0d8c28f2be735ebb1063715e19a6f2cae55753a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Erro: O computador remoto não aparecem em uma caixa de diálogo conexões remotas
Se o computador remoto não for exibido na caixa de diálogo conexões remotas, verifique as seguintes causas comuns.  
  
 Se você estiver usando o modo de compatibilidade gerenciado, verifique a documentação do Visual Studio 2010: [Solucionando problemas de depuração remota - Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Causas comuns desse erro  
  
-   O computador remoto está em execução em um computador que esteja em uma sub-rede diferente. Para corrigir isso, digitar manualmente o nome do computador ou endereço IP na caixa de diálogo de qualificador  
  
-   O depurador remoto não está em execução no computador remoto. Para corrigir isso, inicie o depurador remoto.  
  
-   O firewall está bloqueando a comunicação entre o Visual Studio e o computador remoto. Para corrigir isso, configure o firewall para permitir que o Visual Studio e o depurador remoto (msvsmon) para se comunicar.  
  
-   O software antivírus está bloqueando a comunicação entre o Visual Studio e o computador remoto. Para corrigir isso, configure o software antivírus para permitir que o Visual Studio e o depurador remoto (msvsmon) para se comunicar.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)