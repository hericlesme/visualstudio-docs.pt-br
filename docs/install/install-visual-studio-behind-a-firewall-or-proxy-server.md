---
title: "Instalar o Visual Studio por trás de um firewall ou servidor proxy | Microsoft Docs"
description: 
ms.custom: 
ms.date: 08/01/2017
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
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3862c6ed49e00ffa3800cccbedb2b846823418ed
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Instalar o Visual Studio por trás de um firewall ou servidor proxy

O Instalador do Visual Studio baixa arquivos de vários domínios e seus servidores de download. Esta página lista as URLs de domínio que talvez você queira colocar na "lista de permissões" como confiáveis em seus scripts de implantação.

Se for possível para seu ambiente, considere adicionar os domínios a seguir com os protocolos HTTP e HTTPS.

## <a name="microsoft-domains"></a>Domínios da Microsoft
| Domain | Finalidade |
| ------ | ------- |
| go.microsoft.com | Resolução da URL de instalação |
| aka.ms | Resolução da URL de instalação |
| download.visualstudio.microsoft.com | Local de download de pacotes de instalação |
| download.microsoft.com | Local de download de pacotes de instalação |
| download.visualstudio.com | Local de download de pacotes de instalação |
| dl.xamarin.com | Local de download de pacotes de instalação |
| visualstudiogallery.msdn.microsoft.com | Local de download de extensões do Visual Studio |
| www.visualstudio.com | Local da documentação |
| docs.microsoft.com | Local da documentação |
| msdn.microsoft.com | Local da documentação |
| www.microsoft.com | Local da documentação |
| *.windows.net | Local de conexão |
| *.microsoftonline.com | Local de conexão |
| *.live.com | Local de conexão |


## <a name="non-microsoft-domains"></a>Domínios que não são da Microsoft
| Domain | Instala essas cargas de trabalho |
| ------ | ------- |
| archive.apache.org |  Desenvolvimento móvel com JavaScript <br />(Cordova) |
| cocos2d-x.org | Desenvolvimento de jogos com C++ <br />(Cocos) |
| download.epicgames.com | Desenvolvimento de jogos com C++ <br />(Unreal Engine) |
| download.oracle.com | Desenvolvimento móvel com JavaScript <br />(SDK do Java) <br /><br />Desenvolvimento móvel com .NET <br />(SDK do Java) |
| download.unity3d.com | Desenvolvimento de jogos com Unity <br />(Unity) |
| netstorage.unity3d.com | Desenvolvimento de jogos com Unity <br /> (Unity) |
| dl.google.com | Desenvolvimento móvel com JavaScript <br />(NDK e SDK do Android, emulador) <br /><br />Desenvolvimento móvel com .NET <br />(NDK e SDK do Android, emulador) |
| www.incredibuild.com | Desenvolvimento de jogos com C++ <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Desenvolvimento de jogos com C++ <br />(IncrediBuild) |
| www.python.org | Desenvolvimento do Python <br />(Python) <br /><br />Ciência de dados e aplicativos analíticos <br />(Python) |

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:
* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
  * [Referência de ID de componente e carga de trabalho](workload-and-component-ids.md)
* [Criar uma instalação de rede do Visual Studio 2017](create-a-network-installation-of-visual-studio.md)
  * [Instalar os certificados necessários para instalação offline do Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Automatizar a instalação do Visual Studio com um arquivo de resposta](automated-installation-with-response-file.md)
* [Chaves de produto automaticamente durante a implantação do Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Definir padrões para implantações empresariais do Visual Studio 2017](set-defaults-for-enterprise-deployments.md)
* [Desabilitar ou mover o cache do pacote](disable-or-move-the-package-cache.md)
* [Atualizar uma instalação em rede do Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Atualizações de controle para implantações do Visual Studio 2017](controlling-updates-to-visual-studio-deployments.md)
* [Ferramentas para detectar e gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)
