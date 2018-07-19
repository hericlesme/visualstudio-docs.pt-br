---
title: Download do depurador remoto
description: Links de download para o depurador remoto
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 987193cb7f78947087c6d387e16261d83a20e7c2
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809230"
---
1.  No dispositivo ou servidor máquina que você deseja depurar (em vez do computador que executa o Visual Studio), obtenha a versão correta das ferramentas remotas.

    |Versão|Link|Observações|
    |-|-|-|
    |Visual Studio 2017 (versão mais recente)|[Ferramentas remotas](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Sempre Baixe a versão correspondente do seu sistema operacional do dispositivo (x x86, x64 ou ARM64). No Windows Server, consulte [desbloquear o download do arquivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obter ajuda para baixar as ferramentas remotas.|
    |Visual Studio 2017 (antiga)|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Ferramentas remotas das verões anteriores do Visual Studio 2017 estão disponíveis no My.VisualStudio.com. Se solicitado, junção de grupo de Visual Studio Dev Essentials gratuito, ou entre com sua assinatura do Visual Studio ID. No Windows Server, consulte [desbloquear o download do arquivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obter ajuda para baixar as ferramentas remotas.|
    |Visual Studio 2015 (antiga)|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, junção de grupo de Visual Studio Dev Essentials gratuito, ou entre com sua assinatura do Visual Studio ID. No Windows Server, consulte [desbloquear o download do arquivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obter ajuda para baixar as ferramentas remotas.|
    |Visual Studio 2013|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Baixar a página na documentação do Visual Studio 2013|
    |Visual Studio 2012|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Baixar a página na documentação do Visual Studio 2012|

2.  Na página de download, escolha a versão das ferramentas que corresponde ao seu sistema operacional (x86, x64, ARM ou ARM64) e baixar as ferramentas remotas.

    > [!IMPORTANT]
    >  Recomendamos que você instale a versão mais recente das ferramentas remotas que corresponde à sua versão do Visual Studio. Versões incompatíveis não são recomendadas. Além disso, você deve instalar as ferramentas remotas que têm a mesma arquitetura de sistema operacional no qual você deseja instalá-lo. Em outras palavras, se você quiser depurar um aplicativo de 32 bits em um computador remoto executando um sistema operacional de 64 bits, você deve instalar a versão de 64 bits das ferramentas remotas no computador remoto.
    >
    >  Depuração no Windows 10 em dispositivos ARM, escolha o download do ARM64 disponível com a versão mais recente das ferramentas remotas.  Para dispositivos Windows RT, escolha a versão ARM, que só está disponível no download do Visual Studio 2015 RTW.

3.  Quando você terminar de baixar o arquivo executável, vá para a próxima seção e siga as instruções de instalação.

Se você tentar copiar o depurador remoto (msvsmon.exe) para o computador remoto e executá-lo, esteja ciente de que o **Assistente de configuração do depurador remoto** (**rdbgwiz.exe**) é instalado apenas quando você baixar o ferramentas. Você talvez precise usar o Assistente para configuração mais tarde, especialmente se você deseja que o depurador remoto para ser executado como um serviço. Para obter mais informações, consulte [(opcional) configurar o depurador remoto como um serviço](../../debugger/remote-debugging.md#bkmk_configureService).
