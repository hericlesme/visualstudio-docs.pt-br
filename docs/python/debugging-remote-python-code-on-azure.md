---
title: Depuração remota do Azure com Python
description: Como configurar um Serviço de Aplicativo do Azure para usar o Visual Studio para depuração remota de um aplicativo em Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1e3e70675901128ed6b8d118e54dc10ddee152a5
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008613"
---
# <a name="remotely-debug-python-code-on-azure"></a>Depurar o código do Python remotamente no Azure

O [suporte do Python no Visual Studio](installing-python-support-in-visual-studio.md) inclui a capacidade de depurar remotamente o código do Python em execução no Serviço de Aplicativo do Azure. Ao contrário da depuração remota simples, o computador de destino neste cenário não é diretamente acessível por TCP e, portanto, o Visual Studio fornece um proxy que expõe o protocolo do depurador por HTTP. Os projetos criados com o modelo da Web configuram esse proxy automaticamente no arquivo *web.debug.config* gerado. A depuração remota também é habilitada quando você publica uma configuração **Depuração** do projeto, conforme descrito em [Publicar no Serviço de Aplicativo do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md).

Como a depuração remota do Azure usa soquetes da Web, os soquetes precisam ser habilitados para o Serviço de Aplicativo por meio do [portal do Azure](https://portal.azure.com), acessando **Configurações** > **Configurações de aplicativo**, definindo **Configurações gerais** > **Soquetes da Web** como **Ativado** e selecionando **Salvar** para aplicar a alteração. (Observe que as configurações **Depuração** não se aplicam à depuração do Python.)

![Habilitando soquetes da Web no portal do Azure](media/azure-remote-debugging-enable-web-sockets.png)

## <a name="attach-with-server-explorer"></a>Anexar com o Gerenciador de Servidores

Depois que o projeto for implantado corretamente e os soquetes da Web forem habilitados, você poderá se anexar ao Serviço de Aplicativo no **Gerenciador de Servidores** no Visual Studio (**Exibir** > **Gerenciador de Servidores**). Localize seu site em **Azure** > **Serviço de Aplicativo** e o grupo de recursos aplicável, clique com o botão direito do mouse e selecione **Anexar Depurador (Python)**. (O comando **Anexar Depurador** destina-se a aplicativos .NET em execução no IIS e é útil apenas se você co-hospedar o código .NET junto com o aplicativo do Python.)

O Visual Studio levará você diretamente a um conjunto de instruções para a anexação direta, conforme descrito abaixo em [Anexar sem o Gerenciador de Servidores](#attach-without-server-explorer). Se o comando **Anexar Depurador (Python)** não for exibido ou o Visual Studio não conseguir se anexar ao seu site, confira [Solução de problemas da depuração remota do Python e do Azure](debugging-remote-python-code-on-azure-troubleshooting.md).

Se a anexação for bem-sucedida, o Visual Studio alternará para uma exibição de depurador. A barra de ferramentas indica o processo que está sendo depurado como um URI `wss://`:

![Depurando um site do Serviço de Aplicativo do Azure](media/azure-remote-debugging-attached.png)

Depois de anexada, a experiência de depuração ocorre, basicamente, da mesma maneira que a depuração remota normal, sujeita a algumas restrições. Em particular, o servidor Web do IIS que manipula as solicitações de entrada e as delega ao código do Python por meio do FastCGI tem um tempo limite para a manipulação de solicitação, que usa como padrão 90 segundos. Se a manipulação de solicitação levar mais tempo do que o tempo limite (por exemplo, devido a um processo em pausa em um ponto de interrupção), o IIS encerrará o processo, encerrando a sessão de depuração. 

## <a name="attach-without-server-explorer"></a>Anexar sem o Gerenciador de Servidores

Para anexar o depurador diretamente ao Serviço de Aplicativo, siga as instruções fornecidas na página de informações do proxy WebSocket que é implantado no site pelo Visual Studio em *\<site_url>/ptvsd*, como *ptvsdemo.azurewebsites.net/ptvsd*. Ao visitar essa página, também é verificado se o proxy está configurado corretamente:

![Página de informações do proxy de depuração remota do Azure](media/azure-remote-debugging-proxy-info-page.png)

Conforme indicado, construa uma URL usando o segredo de *web.debug.config*, que é regenerado sempre que o projeto é publicado. Esse arquivo está oculto por padrão no **Gerenciador de Soluções** e não está incluído no projeto; portanto, mostre todos os arquivos ou abra-o em um editor separado. Depois de abrir o arquivo, observe o valor da appSetting chamada `WSGI_PTVSD_SECRET`:

![Determinando o ponto de extremidade do depurador em um Serviço de Aplicativo do Azure](media/azure-remote-debugging-secret.png)

A URL necessária agora está no formato `wss://<secret>@<site_name>.azurewebsites.net/ptvsd`. Substitua &lt;secret&gt; e &lt;site_name&gt; da cadeia de caracteres pelos valores específicos.

Para anexar o depurador, selecione **Depurar** > **Anexar ao Processo**, selecione **Depuração remota do Python** no menu suspenso **Transporte**, insira a URL na **Caixa de texto qualificadora** e pressione **Enter**. Se o Visual Studio puder se conectar com êxito ao Serviço de Aplicativo, ele mostrará um único processo do Python na lista. Selecione-o e, em seguida, **Anexar** para iniciar a depuração:

![Usando a caixa de diálogo Anexar ao Processo para se anexar a um site do Azure](media/azure-remote-debugging-manual-attach.png)
