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
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768216"
---
Estas etapas mostram apenas uma configuração básica do IIS. Para obter informações mais detalhadas ou para instalar em uma máquina de área de trabalho do Windows, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) ou [IIS 8.0 usando ASP.NET 3.5 e o ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Para sistemas operacionais Windows Server, use o **adicionar funções e recursos** Assistente por meio de **gerenciar** link ou o **painel** link no **doGerenciadordeservidores**. Na etapa **Funções de Servidor**, marque a caixa de **Servidor Web (IIS)**.

![A função de Servidor Web IIS é selecionada na etapa Selecionar funções de servidor.](../media/remotedbg-server-roles-ws2012.png)

Na etapa **Serviços de função**, selecione os serviços de função do IIS desejados ou aceite os serviços de função padrão fornecidos. Se você deseja habilitar a implantação usando Publicar configurações e a implantação da Web, certifique-se de que **ferramentas e Scripts de gerenciamento do IIS** está selecionado.

Continue com as etapas de confirmação para instalar a função de servidor web e serviços. Uma reinicialização do servidor/IIS não é necessária após a instalação da função do Servidor Web (IIS).