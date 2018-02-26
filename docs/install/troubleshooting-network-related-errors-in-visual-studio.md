---
title: "Solução de erros relacionados à rede ao instalar ou usar o Visual Studio | Microsoft Docs"
description: 
ms.custom: 
ms.date: 02/12/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d4d1e330a6ab378c61876b3f869f88b2a29c35a1
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Solução de erros relacionados à rede ao instalar ou usar o Visual Studio
Temos soluções para os erros mais comuns relacionadas à rede ou ao proxy que você pode encontrar ao instalar ou usar o Visual Studio atrás de um firewall ou um servidor proxy.

## <a name="error-proxy-authorization-required"></a>Erro: “Autorização de proxy necessária”

Esse erro geralmente ocorre quando os usuários estão conectados à Internet por meio de um servidor proxy e o servidor proxy bloqueia as chamadas que o Visual Studio faz para alguns recursos de rede.

### <a name="to-fix-this-error"></a>Para corrigir esse erro:

- Reinicie o Visual Studio. Uma caixa de diálogo de autenticação de proxy deverá aparecer. Insira suas credenciais na caixa de diálogo quando solicitado.

- Se reiniciar o Visual Studio não resolver o problema, talvez o servidor proxy não solicite credencias para endereços http:&#47;&#47;go.microsoft.com, mas solicite para endereços &#42;.visualStudio.com. Para esses servidores, considere adicionar à lista de permissões as seguintes URLs para desbloquear todos os cenários de conexão no Visual Studio:

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- Caso contrário, você pode remover o endereço de http:&#47;&#47;go.microsoft.com da lista de permissões para que a caixa de diálogo de autenticação de proxy apareça tanto para o endereço http:&#47;&#47;go.microsoft.com quanto para os pontos de extremidade do servidor quando o Visual Studio for reiniciado.

    OU

- Se você quiser usar suas credenciais padrão com o proxy, poderá realizar as seguintes ações:

    1. Localize **devenv.exe.config** (o arquivo de configuração devenv.exe) em: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** ou em **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

    1. No arquivo de configuração, localize o bloco `<system.net>` e adicione esse código:

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        Você deve inserir o endereço de proxy correto para sua rede na `proxyaddress="<http://<yourproxy:port#>`.

    OU

- Você também pode seguir as instruções na postagem no blog [How to connect through an authenticated Web Proxy](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) (Como se conectar por meio de um Proxy Web autenticado), que mostra como adicionar código que permitirá que você use o proxy.

## <a name="error-the-underlying-connection-was-closed"></a>Erro: “A conexão subjacente estava fechada”

Se você estiver usando o Visual Studio em uma rede privada que tem um firewall, o Visual Studio poderá não ser capaz de se conectar a alguns recursos da rede. Esses recursos podem incluir o VSTS (Visual Studio Team Services) para conexão e licenciamento, o NuGet e os serviços do Azure. Se o Visual Studio falhar ao se conectar a um desses recursos, você deverá ver a seguinte mensagem de erro:

  **A conexão subjacente estava fechada: Ocorreu um erro inesperado no envio**

O Visual Studio usa o TLS (protocolo TLS) 1.2 para se conectar aos recursos de rede. Os dispositivos de segurança de algumas redes privadas bloqueiam determinadas conexões de servidor quando o Visual Studio usa o protocolo TLS 1.2.

### <a name="to-fix-this-error"></a>Para corrigir esse erro:

Habilite as conexões para as seguintes URLs:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (para conexões do Azure)

- &#42;.visualstudio.com

- cdn.vsassets.io (hospeda conteúdo da rede de distribuição de conteúdo ou CDN)

- &#42;.gallerycdn.vsassets.io (hospeda extensões do VSTS)

- static2.sharepointonline.com (hospeda recursos que o Visual Studio usa no kit do Office UI Fabric, como fontes)

- &#42;.nuget.org (para conexões NuGet)

 > [!NOTE]
 > As URLs de servidor NuGet privadas podem não estar incluídas nesta lista. Você pode verificar os servidores NuGet que estamos usando em %APPData%\Nuget\NuGet.Config.


## <a name="get-support"></a>Obter suporte
Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas de instalação ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:
* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também
* [Instalar e usar o Visual Studio atrás de um firewall ou servidor proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Instalar o Visual Studio 2017](install-visual-studio.md)
