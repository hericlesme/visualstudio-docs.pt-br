---
title: "Corrigindo os erros de autorização de proxy necessários | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e33e0e2896ccb3a5f7fe6d6da57f509af30d77fe
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="proxy-authorization-required"></a>Autorização de proxy necessária

Esse erro geralmente ocorre quando os usuários estão conectados à Internet por meio de um servidor proxy e o servidor proxy bloqueia as chamadas que o Visual Studio faz para alguns recursos de rede.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Reinicie o Visual Studio. Uma caixa de diálogo de autenticação de proxy deverá aparecer. Insira suas credenciais na caixa de diálogo.

- Se a etapa acima não resolver o problema, pode ser porque o servidor proxy não solicita credenciais para endereços http://go.microsoft.com, mas solicita para endereços *.visualStudio.com. Para esses servidores, você precisa colocar a seguinte lista de URLs na lista de permissões para desbloquear todos os cenários de conexão no Visual Studio:

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- Caso contrário, você pode remover o endereço de http://go.microsoft.com da lista de permissões para que a caixa de diálogo de autenticação de proxy apareça tanto para o endereço http://go.microsoft.com quanto para os pontos de extremidade do servidor quando o Visual Studio for reiniciado.

    OU

- Se você quiser usar suas credenciais padrão com o proxy, poderá fazer o seguinte:

    1. Localize **devenv.exe.config** (o arquivo de configuração devenv.exe) em: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** ou em **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

    1. No arquivo de configuração, localize o bloco `<system.net>` e adicione esse código:

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        Você deve inserir o endereço de proxy correto para sua rede na `proxyaddress="<http://<yourproxy:port#>`.

    OU

- Você também pode seguir as instruções [nesta postagem](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) para adicionar o código que permitirá o uso do proxy.
