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
ms.openlocfilehash: b16c0627fbebf13566726a7f4bfb56ecb2e6a64a
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2018
---
1.  No dispositivo ou servidor máquina que você deseja depurar (em vez do computador executando o Visual Studio), obtenha a versão correta das ferramentas remotas.

    |Versão|Link|Observações|
    |-|-|-|
    |Visual Studio 2017 (versão mais recente)|[Ferramentas remotas](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|Sempre Baixe a versão correspondente de seu sistema operacional do dispositivo (x86 ou x64). Se o modo de segurança aprimorada estiver ativado (Windows Server), você deve adicionar novos sites confiáveis se solicitado.|
    |Visual Studio de 2017 (antiga)|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Ferramentas remotas para versões anteriores do Visual Studio de 2017 estão disponíveis no My.VisualStudio.com. Se solicitado, associação a grupo livre de Fundamentos de desenvolvimento do Visual Studio, ou entre com sua assinatura do Visual Studio ID. Se o modo de segurança aprimorada estiver ativado (Windows Server), você deve adicionar novos sites confiáveis se solicitado.|
    |Visual Studio 2015 Atualização 3|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, associação a grupo livre de Fundamentos de desenvolvimento do Visual Studio, ou entre com sua assinatura do Visual Studio ID. Se o modo de segurança aprimorada estiver ativado (Windows Server), você deve adicionar novos sites confiáveis se solicitado.|
    |Visual Studio 2015 (older)|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, associação a grupo livre de Fundamentos de desenvolvimento do Visual Studio, ou entre com sua assinatura do Visual Studio ID. Se o modo de segurança aprimorada estiver ativado (Windows Server), você deve adicionar novos sites confiáveis se solicitado.|
    |Visual Studio 2013|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Baixar página na documentação do Visual Studio 2013|
    |Visual Studio 2012|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Baixar página na documentação do Visual Studio 2012|
  
2.  Na página de download, escolha a versão das ferramentas que corresponde ao seu sistema operacional (x 86, x64 ou ARM) e baixar as ferramentas remotas.
  
    > [!IMPORTANT]
    >  Recomendamos que você instale a versão mais recente das ferramentas remotas que corresponde à sua versão do Visual Studio. Versões não correspondentes não são recomendadas. Além disso, você deve instalar as ferramentas remotas que têm a mesma arquitetura do sistema operacional no qual você deseja instalá-lo. Em outras palavras, se você quiser depurar um aplicativo de 32 bits em um computador remoto executando um sistema operacional de 64 bits, você deve instalar a versão de 64 bits das ferramentas remotas no computador remoto. 
    >   
    >  Superfície 3 alternado do ARM para x64 arquitetura. Uma versão ARM das ferramentas remotas não está disponível para o Visual Studio de 2017. Para Visual Studio 2015, localize a versão do ARM no download RTW de 2015 do Visual Studio.
  
3.  Quando você terminar de baixar o arquivo executável, vá para a próxima seção e siga as instruções de instalação.

Se você tentar copiar o depurador remoto (msvsmon.exe) para o computador remoto e executá-lo, esteja ciente de que o **Assistente de configuração do depurador remoto** (**rdbgwiz.exe**) é instalado apenas quando você baixar o ferramentas. Talvez seja necessário usar o Assistente para configuração mais tarde, especialmente se você deseja que o depurador remoto para ser executado como um serviço. Para obter mais informações, consulte [(opcional) configurar o depurador remoto como um serviço](../../debugger/remote-debugging.md#bkmk_configureService).
