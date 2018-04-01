---
title: Perguntas Frequentes de depuração de instantâneo | Microsoft Docs
ms.date: 11/07/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fd2ca2bf48c50b0ea5b44654d0711ba162313f04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Perguntas frequentes para instantâneo de depuração no Visual Studio

Aqui está uma lista de perguntas que podem surgir durante a depuração de aplicativos do Azure ao vivo usando o depurador do instantâneo.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>O que é o custo de desempenho de tirar um instantâneo?

Quando o depurador de instantâneo captura um instantâneo do seu aplicativo, é bifurcação de processo do aplicativo e a cópia bifurcada a suspensão. Quando você depura um instantâneo, você está depurando em relação a cópia bifurcada do processo. Esse processo leva apenas 10 a 20 milissegundos, mas não copia o heap completas do aplicativo; em vez disso, ele copia apenas a tabela de página e define páginas de cópia na gravação. Se alguns dos objetos do aplicativo sobre a alteração do heap, suas páginas respectivas são copiadas. Cada instantâneo, portanto, tem um custo de memória muito pequeno (na ordem de centenas de kilobytes para a maioria dos aplicativos). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>O que acontece se eu tiver um serviço de aplicativo do Azure expandido (várias instâncias do meu aplicativo)?

Quando você tiver várias instâncias do seu aplicativo, snappoints serão aplicadas a cada instância única. Somente o primeiro snappoint para atingir com as condições especificadas cria um instantâneo. Se você tiver vários snappoints, instantâneos subsequentes vêm da mesma instância que criou o primeiro instantâneo. Logpoints enviados à janela saída mostrará apenas as mensagens de uma instância, enquanto logpoints enviados para os logs de aplicativo enviar mensagens de cada instância. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Como o depurador de instantâneo carregar símbolos?

O depurador de instantâneo requer que você tenha os símbolos correspondentes para seu aplicativo ou localmente ou implantado em seu serviço de aplicativo do Azure (PDBs incorporados não há suporte atualmente). O depurador de instantâneo baixa automaticamente os símbolos do seu serviço de aplicativo do Azure. A partir do Visual Studio de 2017 versão 15.2, implantação do serviço de aplicativo do Azure também implanta os símbolos do seu aplicativo.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>O depurador de instantâneo funciona em compilações de lançamento do meu aplicativo?

Sim - o depurador de instantâneo destina-se para trabalhar em compilações de versão. Quando um snappoint é colocado em uma função, a função é recompilada para uma versão de depuração, facilitando depurável. Quando você interrompe o depurador de instantâneo, as funções são retornadas ao seu build de versão. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Logpoints podem causar efeitos colaterais no meu aplicativo de produção?

Não - quaisquer mensagens de log que você adicionar ao seu aplicativo são avaliadas virtualmente. Eles não podem causar efeitos colaterais em seu aplicativo. No entanto, algumas propriedades nativas podem não estar acessíveis com logpoints. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>O depurador de instantâneo funciona se o servidor está sob carga?

Sim, a depuração de instantâneo pode trabalhar para servidores sob carga. O depurador do instantâneo limita e não capturar instantâneos em situações em que há uma quantidade pequena de memória livre no servidor.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Como desinstalar o depurador de instantâneo?

Você pode desinstalar a extensão de site do depurador de instantâneo em seu serviço de aplicativo com as seguintes etapas:

1. Desativar o serviço de aplicativo por meio do Gerenciador de nuvem no Visual Studio ou o Portal do Azure.
1. Navegue até o site de Kudu do seu serviço de aplicativo (ou seja, yourappservice. **SCM**. azurewebsites.net) e navegue até **Site extensões**.
1. Clique no X na extensão de site do depurador de instantâneo para removê-lo.

## <a name="see-also"></a>Consulte também

[Depurando no Visual Studio](../debugger/index.md)  
[Depurar aplicativos do ASP.NET ao vivo usando o depurador do instantâneo](../debugger/debug-live-azure-applications.md)  
[Problemas conhecidos e solução de problemas para depuração de instantâneo](../debugger/debug-live-azure-apps-troubleshooting.md)
