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
ms.openlocfilehash: b6e312f7e1913a8b4533c0127b966dc3ac0d981d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809235"
---
Você deve ter permissões administrativas no computador remoto.  
  
1.  Localize o aplicativo depurador remoto. (Encontrar msvsmon.exe no local em que ele foi instalado, ou abra o menu Iniciar e procure **depurador remoto**.)
  
     Se você estiver executando o depurador remoto em um servidor remoto, você pode o aplicativo depurador remoto com o botão direito e escolha **executar como administrador**. Se você não estiver executando-lo em um servidor remoto, apenas iniciá-lo normalmente.
  
3.  Ao iniciar as ferramentas remotas pela primeira vez (ou antes que você tenha configurado para isso), o **configuração de depuração remota** caixa de diálogo é exibida.  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Se a API de serviço do Windows não está instalada (o que ocorre apenas no Windows Server 2008 R2), escolha o **instalar** botão.  
  
5.  Selecione os tipos de rede que você deseja usar as ferramentas remotas no. Pelo menos um tipo de rede deve ser selecionado. Se os computadores estiverem conectados por meio de um domínio, você deve escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo de trabalho ou um grupo doméstico, você precisa escolher o item de segundo ou terceiro conforme apropriado.  
  
6.  Escolher **configurar a depuração remota** para configurar o firewall e iniciar a ferramenta.  
  
7.  Quando a configuração estiver concluída, a janela do depurador remoto é exibida.
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     O depurador remoto agora está aguardando uma conexão. Anote o nome do servidor e o número da porta que é exibido, como isso deve corresponder a configuração que você usa mais tarde no Visual Studio.  
  
 Quando você terminar a depuração e a necessidade de parar o depurador remoto, clique em **arquivo > Sair** na janela. Você pode reiniciá-lo partir o **iniciar** menu ou da linha de comando:  
  
 **\<Diretório de instalação do depurador remoto >\\< x86, x64, ARM, ARM64 ou Appx > \msvsmon.exe**.  
