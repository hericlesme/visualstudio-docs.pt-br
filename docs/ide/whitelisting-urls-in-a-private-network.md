---
title: "Lista de URLs com permissão em uma rede privada | Microsoft Docs"
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4a4093c7ebba74493a64833bfbf83ee6d28ef1ef
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="whitelisting-urls-in-a-private-network"></a>Lista de URLs com permissão em uma rede privada

Se você estiver usando o Visual Studio em uma rede privada que usa um dispositivo de segurança, como um firewall, o Visual Studio poderá não ser capaz de se conectar a alguns recursos da rede. Esses recursos incluem o VSTS (Visual Studio Team Services) para conexão e licenciamento, o NuGet e os serviços do Azure. Se o Visual Studio falhar ao se conectar a um desses recursos, você verá a seguinte mensagem de erro:

  **A conexão subjacente estava fechada: Ocorreu um erro inesperado no envio**

O Visual Studio usa o TLS (protocolo TLS) 1.2 para se conectar aos recursos de rede. Os dispositivos de segurança de algumas redes privadas bloqueiam determinadas conexões de servidor quando o Visual Studio usa o protocolo TLS 1.2. Para corrigir o erro, habilite as conexões para as seguintes URLs:

- https://management.core.windows.net

- https://app.vssps.visualstudio.com

- https://login.microsoftonline.com

- https://login.live.com

- https://go.microsoft.com

- https://graph.windows.net

- https://app.vsspsext.visualstudio.com

- *.azurewebsites.net (para conexões do Azure)

- *.nuget.org (para conexões do NuGet)

- *.visualstudio.com

- cdn.vsassets.io (hospeda conteúdo da rede de distribuição de conteúdo ou CDN)

- *.gallerycdn.vsassets.io (hospeda extensões do VSTS)

- static2.sharepointonline.com (hospeda recursos que o Visual Studio usa no kit de interface do usuário da malha do office, como fontes)

> [!NOTE]
> As URLs de servidor NuGet privadas podem não estar incluídas na lista acima. Você pode verificar os servidores NuGet que estão sendo usados, ao abrir %APPData%\Nuget\NuGet.Config.

## <a name="see-also"></a>Consulte também

[Erro de autorização de proxy necessária](../ide/reference/proxy-authorization-required.md)  
[Instalar o Visual Studio por trás de um firewall ou servidor proxy](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)
