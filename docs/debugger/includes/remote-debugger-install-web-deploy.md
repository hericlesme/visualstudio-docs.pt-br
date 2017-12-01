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
ms.openlocfilehash: 81b58a2162d7240e32e1fb2d45e462ec551155e7
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2017
---
1. Se você pretende implantar seus aplicativos com a implantação da Web no Visual Studio, instale a versão mais recente da implantação da Web no servidor.

    Para instalar a implantação da Web, use o [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Implantação da Web você encontrar na guia aplicativos. Você também pode obter um instalador diretamente a partir de [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Verificar se implantação da Web está funcionando corretamente abrindo **painel de controle > sistema e segurança > Ferramentas administrativas > serviços** e certifique-se de que **o serviço de agente de implantação Web** está em execução (a nome do serviço é diferente em versões mais antigas).

    Se o serviço de agente não está em execução, inicie-o. Se não estiver presente em todos os, vá para **painel de controle > Programas > desinstalar um programa**, localizar **Microsoft Web Deploy <version>** . Escolha a **alteração** a instalação e certifique-se de que você escolha **será instalado na unidade de disco rígido local** para os componentes de implantação da Web. Conclua as etapas de instalação de alteração.