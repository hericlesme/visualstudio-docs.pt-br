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
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2018
---
1. Se você pretende implantar seus aplicativos com a implantação da Web no Visual Studio, instale a versão mais recente da implantação da Web no servidor.

    Para instalar a implantação da Web, use o [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Para localizar o link do instalador de plataforma da Web do IIS, selecione **IIS** no painel esquerdo do Gerenciador do servidor. O servidor e selecione **serviços de informações da Internet (IIS) Manager**.)

    O Web Platform Installer, você encontrará implantação da Web na guia aplicativos. Você também pode obter um instalador diretamente a partir de [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Verificar se implantação da Web está funcionando corretamente abrindo **painel de controle > sistema e segurança > Ferramentas administrativas > serviços** e certifique-se de que **o serviço de agente de implantação Web** está em execução (a nome do serviço é diferente em versões mais antigas).

    Se o serviço de agente não está em execução, inicie-o. Se não estiver presente em todos os, vá para **painel de controle > Programas > desinstalar um programa**, localizar **Microsoft Web Deploy <version>** . Escolha a **alteração** a instalação e certifique-se de que você escolha **será instalado na unidade de disco rígido local** para os componentes de implantação da Web. Conclua as etapas de instalação de alteração.