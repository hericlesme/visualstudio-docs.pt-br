---
title: Criar uma instalação offline do Visual Studio | Microsoft Docs
description: Saiba como instalar o Visual Studio offline.
ms.custom: ''
ms.date: 01/17/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 116e1821575b1a5e4e95e43eed0f175d85e9278f
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Criar uma instalação offline do Visual Studio 2017

Projetamos o instalador do Visual Studio 2017 para funcionar bem em uma ampla variedade de condições de rede e computador.

- O novo modelo com base em cargas de trabalho significa que você precisará baixar bem menos que nas versões anteriores do Visual Studio: apenas 300 MB para a instalação menor;
- Em comparação com um arquivo zip ou "ISO" genérico, somente os pacotes necessários são baixados para o computador. Por exemplo, não baixe arquivos de 64 bits se não precisar deles;
- Durante o processo de instalação, tentamos três tecnologias de download diferentes (WebClient, BITS e WinInet) para minimizar a interferência com o software antivírus e proxy;
- Os arquivos de que você precisará para instalar o Visual Studio são distribuídos em uma rede de distribuição global. Portanto, é possível obtê-lo para você de um servidor local.

Recomendamos que você experimente o [instalador da Web do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)&mdash;, pois acreditamos que ele lhe proporcionará uma boa experiência.

 > [!div class="button"]
 > [Baixe o Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Se você deseja instalar offline porque sua conexão com a Internet está indisponível ou não é confiável, consulte [Instalar o Visual Studio 2017 em ambientes de rede não confiável ou de baixa largura de banda](../install/install-vs-inconsistent-quality-network.md). Você pode usar a linha de comando para criar um cache local dos arquivos necessários para concluir uma instalação offline. Esse processo substitui os arquivos ISO disponíveis de versões anteriores.

> [!NOTE]
> Se você for um administrador de empresas que deseja executar uma implantação do Visual Studio 2017 em uma rede de estações de trabalho cliente protegidas da Internet por firewall, confira nossas páginas [Criar uma instalação de rede do Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Instalar os certificados necessários para a instalação offline do Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:
* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opção requer uma conta do [GitHub](https://github.com/).)
