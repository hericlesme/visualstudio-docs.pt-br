---
title: Criar uma instalação offline do Visual Studio
description: Saiba como instalar o Visual Studio offline.
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: d19eabe10234ca2a1670ae04f99a45a85a6cac14
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138871"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Criar uma instalação offline do Visual Studio 2017

Projetamos o instalador do Visual Studio 2017 para funcionar bem em uma ampla variedade de condições de rede e computador.

- O novo modelo com base em cargas de trabalho significa que você precisará baixar bem menos que nas versões anteriores do Visual Studio: apenas 300 MB para a instalação menor;
- Em comparação com um arquivo zip ou "ISO" genérico, somente os pacotes necessários são baixados para o computador. Por exemplo, não baixe arquivos de 64 bits se não precisar deles;
- Durante o processo de instalação, tentamos três tecnologias de download diferentes (WebClient, BITS e WinInet) para minimizar a interferência com o software antivírus e proxy;
- Os arquivos de que você precisará para instalar o Visual Studio são distribuídos em uma rede de distribuição global. Portanto, é possível obtê-lo para você de um servidor local.

Recomendamos que você experimente o [instalador da Web do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;, pois acreditamos que ele lhe proporcionará uma boa experiência.

 > [!div class="button"]
 > [Baixe o Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Se você deseja instalar offline porque sua conexão com a Internet está indisponível ou não é confiável, consulte [Instalar o Visual Studio 2017 em ambientes de rede não confiável ou de baixa largura de banda](../install/install-vs-inconsistent-quality-network.md). Você pode usar a linha de comando para criar um cache local dos arquivos necessários para concluir uma instalação offline. Esse processo substitui os arquivos ISO disponíveis de versões anteriores.

> [!NOTE]
> Se você for um administrador de empresas que deseja executar uma implantação do Visual Studio 2017 em uma rede de estações de trabalho cliente protegidas da Internet por firewall, confira nossas páginas [Criar uma instalação de rede do Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Instalar os certificados necessários para a instalação offline do Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]
