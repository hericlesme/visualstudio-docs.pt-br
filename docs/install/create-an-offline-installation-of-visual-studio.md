---
title: "Criar uma instalação offline do Visual Studio | Microsoft Docs"
description: Saiba como instalar o Visual Studio offline.
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 8b0902c7e2d3c2b51ecd915647a3e8a03e49c641
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Criar uma instalação offline do Visual Studio 2017

Projetamos o instalador do Visual Studio 2017 para funcionar bem em uma ampla variedade de condições de rede e computador.

- O novo modelo com base em cargas de trabalho significa que você precisará baixar bem menos que nas versões anteriores do Visual Studio: apenas 300 MB para a instalação menor;
- Em comparação com um arquivo zip ou "ISO" genérico, somente os pacotes necessários são baixados para o computador. Por exemplo, não baixe arquivos de 64 bits se não precisar deles;
- Durante o processo de instalação, tentamos três tecnologias de download diferentes (WebClient, BITS e WinInet) para minimizar a interferência com o software antivírus e proxy.
- Os arquivos de que você precisará para instalar o Visual Studio são distribuídos em uma rede de distribuição global. Portanto, é possível obtê-lo para você de um servidor local.

Recomendamos que você experimente o [instalador da Web do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)&mdash;, pois acreditamos que ele lhe proporcionará uma boa experiência.

 > [!div class="button"]
 > [Baixe o Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Se você deseja instalar offline porque sua conexão com a Internet está indisponível ou não é confiável, consulte [Instalar o Visual Studio 2017 em ambientes de rede não confiável ou de baixa largura de banda](../install/install-vs-inconsistent-quality-network.md). Você pode usar a linha de comando para criar um cache local dos arquivos necessários para concluir uma instalação offline. Esse processo substitui os arquivos ISO disponíveis de versões anteriores.

> [!NOTE]
> Se você for um administrador de empresas que deseja executar uma implantação do Visual Studio 2017 em uma rede de estações de trabalho cliente protegidas por um firewall da Internet, consulte nossas páginas [Criar uma instalação de rede do Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Considerações especiais para a instalação do Visual Studio em um ambiente offline](../install/install-visual-studio-in-offline-environment.md).

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, consulte a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md) para obter dicas de solução de problemas. Além disso, você pode relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), no IDE do Visual Studio ou compartilhar uma sugestão conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579). É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas. Também é possível interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio) (exige uma conta do [GitHub](https://github.com/)).
