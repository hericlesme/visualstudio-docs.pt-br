---
title: Gerenciando referências em um projeto
description: Este artigo descreve como gerenciar referências em um projeto no Visual Studio para Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 82875955e861ec25e1444874afaa8b7f2e807fa7
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="managing-references-in-a-project"></a>Gerenciando referências em um projeto

O Visual Studio para Mac fornece dois meios de acrescentar referências adicionais ao seu projeto:

![Referências de Projeto](media/projects-and-solutions-image10.png)

Elas são:

* Referências
* NuGets (adicionado por meio da pasta Pacotes)

Além disso, as referências Web e nativas também podem ser adicionadas a qualquer projeto.

## <a name="assembly-references"></a>Referências de assembly

Cada estrutura do Xamarin é fornecida com diversos assemblies. Nem todos esses pacotes de assembly são referenciados no seu projeto por padrão. 

Para editar pacotes que são referenciados no seu projeto, use a caixa de diálogo _Editar Referências_, que é exibida clicando duas vezes na pasta Referências ou selecionando Editar Referências em suas ações do menu de contexto:

![Caixa de diálogo Referências do assembly](media/projects-and-solutions-image11.png)

Para obter informações sobre os assemblies disponíveis para cada estrutura d Xamarin, consulte o guia [Assemblies disponíveis](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet é o gerenciador de pacote mais popular para desenvolvimento .NET. O NuGet do Visual Studio para Mac permite que você pesquise pacotes para adicionar ao seu projeto.

Para fazer isso, clique com o botão direito na pasta **Pacote** no Painel de Soluções e selecione Adicionar Pacotes.

Mais informações sobre como usar um pacote NuGet são fornecidas no passo a passo [Incluindo pacote NuGet no seu projeto](nuget-walkthrough.md).
