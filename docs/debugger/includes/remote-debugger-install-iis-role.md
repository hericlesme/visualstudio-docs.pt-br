---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 103cefa8573c8f44efff0b53b0c09a5ec26706e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
Estas etapas mostram apenas uma configuração básica do IIS. Para obter informações mais detalhadas ou para instalar em uma máquina de área de trabalho do Windows, consulte [publicar no IIS](https://docs.microsoft.com/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) ou [IIS 8.0 usando ASP.NET 3.5 e o ASP.NET 4.5](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Para sistemas operacionais Windows Server, use o **adicionar funções e recursos** Assistente por meio de **gerenciar** link ou o **painel** link no **doGerenciadordeservidores**. Na etapa **Funções de Servidor**, marque a caixa de **Servidor Web (IIS)**.

![A função de Servidor Web IIS é selecionada na etapa Selecionar funções de servidor.](../media/remotedbg-server-roles-ws2012.png)

Na etapa **Serviços de função**, selecione os serviços de função do IIS desejados ou aceite os serviços de função padrão fornecidos.

Continue com as etapas de confirmação para instalar a função de servidor web e serviços. Uma reinicialização do servidor/IIS não é necessária após a instalação da função do Servidor Web (IIS).