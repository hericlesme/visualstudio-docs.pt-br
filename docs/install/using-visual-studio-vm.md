---
title: "Usar o Visual Studio em uma máquina virtual do Azure | Microsoft Docs"
description: "Saiba como usar o Visual Studio de uma máquina virtual do Azure"
ms.date: 01/30/2018
ms.technology: vs-acquisition
ms.topic: article
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: phillee
manager: sacalla
ms.workload:
- multiple
ms.openlocfilehash: d8e99965867d5dbc2710d6c56c5b3dc90fc16dc8
ms.sourcegitcommit: 4b4027244b8de25e30b533148804b87321d3e8a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a id="top"> </a> Imagens do visual Studio no Azure
Usar o Visual Studio em execução em uma VM (máquina virtual) do Azure pré-configurada é a maneira mais fácil e rápida de partir do nada para um ambiente de desenvolvimento em execução.  Há imagens do sistema com configurações diferentes do Visual Studio disponíveis no [Azure Marketplace](https://portal.azure.com/). Apenas reinicie uma VM e pronto.

Novo usuário do Azure? [Crie uma conta gratuita do Azure](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Quais configurações e versões estão disponíveis?
No Azure Marketplace, você encontra imagens para as versões principais mais recentes: Visual Studio 2017 e Visual Studio 2015.  Para cada versão principal, você vê a versão lançada originalmente (também conhecida como "RTW") e as versões atualizadas "mais recentes".  Para cada uma dessas versões diferentes, você encontra as edições do Visual Studio Enterprise e do Visual Studio Community.  Atualizamos essas imagens pelo menos uma vez por mês para incluir as atualizações mais recentes do Visual Studio e do Windows.  Embora os nomes das imagens permaneçam os mesmos, a descrição de cada imagem inclui a versão instalada do produto e a data "desde" da imagem.

|               Versão de lançamento              |        Edições       |     Versão do produto     |
|:------------------------------------------:|:---------------------:|:-----------------------:|
| Visual Studio 2017 – Mais recente (versão 15,5) | Enterprise, Community |      Versão 15.5.3     |
|         Visual Studio 2017 – RTW           | Enterprise, Community |      Versão 15.0.7     |
|   Visual Studio 2015 – Mais recente (Atualização 3)   | Enterprise, Community |  Versão 14.0.25431.01  |
|         Visual Studio 2015 – RTW           |         Nenhum          | (Expirado para manutenção) |

> [!NOTE]
> De acordo com a política de manutenção da Microsoft, a versão lançada originalmente (também conhecida como "RTW") do Visual Studio 2015 expirou para manutenção.  Portanto, o Visual Studio 2015 Atualização 3 é a única versão restante oferecida para a linha de produtos do Visual Studio 2015.

Para saber mais, confira [Política de manutenção do Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Quais recursos estão instalados?
Cada imagem contém o recurso recomendado definido para essa edição do Visual Studio.  Em geral, a instalação inclui:

* Todas as cargas de trabalho disponíveis, incluindo os componentes opcionais recomendados dessa carga de trabalho
* .NET 4.6.2 e .NET 4.7 SDKs, Pacotes de direcionamento e Ferramentas para Desenvolvedores
* Visual F#
* Extensão do GitHub para Visual Studio
* Ferramentas do LINQ to SQL

Essa é a linha de comando que usamos para instalar o Visual Studio ao compilar as imagens:

```
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       add Microsoft.Net.Component.4.7.SDK ^
       add Microsoft.Net.Component.4.7.TargetingPack ^ 
       add Microsoft.Net.Component.4.6.2.SDK ^
       add Microsoft.Net.Component.4.6.2.TargetingPack ^
       add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       add Microsoft.VisualStudio.Component.FSharp ^
       add Component.GitHub.VisualStudio ^
       add Microsoft.VisualStudio.Component.LinqToSql
```

Se as imagens não incluírem um recurso do Visual Studio do qual você precisa, forneça esse comentário por meio da ferramenta de comentários (canto superior direito da página).

## <a name="what-size-vm-should-i-choose"></a>Qual tamanho de VM eu devo escolher?
O provisionamento de uma nova máquina virtual é fácil, e o Azure oferece uma gama completa de tamanhos de máquina virtual.  Assim como acontece com qualquer aquisição de hardware, convém equilibrar o desempenho e o custo.  Como o Visual Studio é um aplicativo multithread poderoso, convém ter um tamanho de VM que inclua pelo menos dois processadores e 7 GB de memória. No Azure, isso se traduz em pelo menos estes tamanhos de VM:

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Para saber mais sobre os tamanhos de máquina mais recentes, veja [Tamanhos de máquinas virtuais do Windows no Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes).

Com o Azure, você não fica preso em sua primeira escolha – você pode reequilibrar sua escolha inicial redimensionando a VM.  Você pode provisionar uma nova VM com um tamanho mais apropriado, ou pode redimensionar a VM existente para um hardware subjacente diferente.  Para saber mais, confira [Redimensionar uma VM do Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/resize-vm).

## <a name="after-i-get-the-vm-running-then-what"></a>Após a execução da VM, o que eu faço?
O Visual Studio segue o modelo "traga a sua própria licença" no Azure.  Portanto, assim como em uma instalação em hardware proprietário, uma das primeiras etapas é o licenciamento de sua instalação do Visual Studio.  Você pode desbloquear o Visual Studio entrando com uma conta da Microsoft associada a uma assinatura do Visual Studio, ou você pode desbloquear o Visual Studio com a chave do produto com sua compra inicial.  Para saber mais, confira [Entrar no Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/signing-in-to-visual-studio) e [Como desbloquear o Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-unlock-visual-studio).

## <a name="after-i-build-out-the-dev-vm-how-do-i-save-capture-it-for-future-or-team-use"></a>Após a compilação da VM de desenvolvimento, como eu salvo (capturo) para uso futuro ou para a equipe?

O espectro de ambientes de desenvolvimento é grande, e não há um custo real associado à compilação de ambientes mais complexos.  No entanto, independentemente da configuração de seu ambiente, o Azure facilita a preservação desse investimento salvando/capturando sua VM perfeitamente configurada como uma "imagem base" para uso futuro – para si mesmo e/ou para outros membros da equipe.  Em seguida, ao inicializar uma nova VM, provisione-a desde a imagem base em vez de a imagem do Marketplace.

Como resumo rápido, você precisará usar sysprep e desligar a VM em execução, depois *capture (Figura 1)* a VM como uma imagem por meio da interface do usuário do Portal do Azure.  O Azure salva o arquivo `.vhd` que contém a imagem na conta de armazenamento de sua escolha.  Em seguida, a nova imagem aparecerá como um recurso de imagem na lista de recursos de sua assinatura.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Figura 1) Capture uma imagem por meio da interface do usuário do Portal do Azure.*</center>

Para saber mais, confira [Capturar uma VM em uma imagem](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource).

  **Lembrete:** não se esqueça de usar sysprep na VM!  Se você ignorar esta etapa, o Azure não poderá provisionar uma VM a partir da imagem.

> [!NOTE]
> Você ainda incorrerá em custos para o armazenamento das imagens, mas provavelmente esse custo incremental será insignificante em comparação aos custos de recursos humanos para recompilar a VM desde o início – para cada pessoa da sua equipe que precise de uma VM.  Por exemplo, custa apenas alguns dólares criar e armazenar uma imagem de 127 GB por um mês que seja reutilizável por todos os membros da equipe.  No entanto, esses custos são insignificantes em comparação com as horas investidas por cada funcionário para compilar e validar uma caixa de desenvolvimento configurada corretamente para o uso individual.

Além disso, talvez as tarefas de desenvolvimento ou as tecnologias precisem de mais escala – como variedades de configurações de desenvolvimento e várias configurações de máquina.  Você pode usar o Azure DevTest Labs para criar _receitas_ que automatizam a construção de sua "imagem dourada" e para gerenciar políticas para as VMs em execução de sua equipe.  [O Azure DevTest Labs para desenvolvedores](https://docs.microsoft.com/en-us/azure/devtest-lab/devtest-lab-developer-lab) é a melhor fonte para obter mais informações sobre o DevTest Labs.

## <a name="next-steps"></a>Próximas etapas
Agora que você já conhece as imagens pré-configuradas do Visual Studio, a próxima etapa é criar uma nova VM:

* [Criar uma VM por meio do Portal do Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)
* [Visão geral das máquinas virtuais do Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/overview)
