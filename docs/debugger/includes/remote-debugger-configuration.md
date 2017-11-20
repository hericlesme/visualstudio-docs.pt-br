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
ms.openlocfilehash: 05a288a2d8dff776d8a5d3faea47b06d101f2ea3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
Você deve ter permissões administrativas no computador remoto.  
  
1.  Localize o aplicativo do depurador remoto. (Localizar msvsmon.exe no local em que ele foi instalado, ou abra o menu Iniciar e procure **depurador remoto**.)
  
     Se você estiver executando o depurador remoto em um servidor remoto, você pode com o botão direito do aplicativo depurador remoto e escolha **executar como administrador**. Se você não estiver executando-lo em um servidor remoto, basta iniciá-lo normalmente.
  
3.  Ao iniciar as ferramentas remotas pela primeira vez (ou antes que você configurou), o **configuração de depuração remota** caixa de diálogo é exibida.  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Se a API de serviço do Windows não está instalada (o que acontece apenas no Windows Server 2008 R2), escolha o **instalar** botão.  
  
5.  Selecione os tipos de rede que você deseja usar as ferramentas remotas em. Pelo menos um tipo de rede deve ser selecionado. Se os computadores são conectados por meio de um domínio, você deve escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo doméstico ou de grupo de trabalho, você precisa escolher o item de segundo ou terceiro conforme apropriado.  
  
6.  Escolha **configurar depuração remota** para configurar o firewall e iniciar a ferramenta.  
  
7.  Quando a configuração estiver concluída, a janela de depurador remoto é exibida.
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     O depurador remoto está aguardando uma conexão. Anote o nome do servidor e a porta de número que é exibido, porque isso deve corresponder à configuração que você usar posteriormente no Visual Studio.  
  
 Quando você terminar de depuração e a necessidade de parar o depurador remoto, clique em **arquivo > Sair** na janela. Você pode reiniciá-lo do **iniciar** menu ou da linha de comando:  
  
 **\<Diretório de instalação do Visual Studio > \Common7\IDE\Remote depurador\\< x86, x64 ou Appx\msvsmon.exe**.  