---
title: Ações de Build
description: Este artigo descreve as diferentes ações de build que podem ser usadas para projetos em C#
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 6ef2cc3347480fceab23df12e53be65dd5432183
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224371"
---
# <a name="build-actions"></a>Ações de Build

Todos os arquivos em um projeto do Visual Studio para Mac tem uma ação de build que controla o que acontece com o arquivo durante um build. Elas podem ser definidas clicando com o botão direito do mouse em qualquer arquivo e navegando para **Ação de Build**, conforme ilustrado abaixo:

![Selecionando ação de compilação de build no Gerenciador de Soluções](media/projects-and-solutions-image1.png)

Algumas das ações de build comuns para projetos C# são:

* **None** – O arquivo não faz parte do build de nenhuma forma, sendo incluído no projeto para fácil acesso do IDE.
* **Compile** – O arquivo será passado para o compilador C# como um arquivo de origem.
* **EmbeddedResource** – O arquivo será passado para o compilador C# como um recurso a ser inserido no assembly. O namespace `System.Reflection` pode ser usado para ler o arquivo do assembly.
* **Content** – Para projetos ASP.NET, esses arquivos serão incluídos como parte do site quando ele for implantado. Para projetos Xamarin.iOS e Xamarin.Mac, eles estarão contidos no lote de aplicativo.

É possível selecionar mais de um arquivo no gerenciador de Soluções, permitindo que você defina a ação de build para vários arquivos ao mesmo tempo.

Além disso, há ações de build para projetos específicos. Por exemplo, projetos Xamarin.iOS têm a ação de build **BundleResource**, que adiciona o arquivo como parte do pacote de aplicativo. Informações sobre as ações de build específicas do Xamarin.Android podem ser encontradas no guia de [processo de build](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).