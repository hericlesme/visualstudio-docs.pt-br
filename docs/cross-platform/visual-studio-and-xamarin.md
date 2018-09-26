---
title: Visual Studio e Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: caf1ea462cc69366f11e4768003707e9cc263327
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495733"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio e Xamarin

O Xamarin é uma plataforma de desenvolvimento de aplicativos móveis para criar aplicativos nativos do iOS, do Android e do Windows usando uma base de código C#/.NET comum. Os aplicativos escritos com o Xamarin podem atingir de 75% a quase 100% de reutilização de código entre as plataformas. Esses aplicativos têm acesso completo às APIs da plataforma subjacente e podem incorporar interfaces do usuário nativos. Eles são compilados para pacotes específicos da plataforma com pouco impacto no desempenho do tempo de execução. (Observação: o Xamarin também dá suporte a F#, mas essa documentação se concentra somente em C#. No momento, não há suporte para o Visual Basic.)

Os desenvolvedores familiarizados com C#, .NET e Visual Studio aproveitam a mesma eficiência e produtividade ao trabalhar com o Xamarin para aplicativos móveis. Esses benefícios incluem a depuração remota em dispositivos Android, iOS e Windows, sem precisar aprender linguagens de codificação nativas como Objective-C ou Java. Portanto, não é surpresa que vários aplicativos de alto desempenho com belas interfaces do usuário, como NASCAR, Aviva e MixRadio, tenham sido criados usando o Xamarin.

Esta documentação ajuda você a avaliar a eficiência total do **Visual Studio com o Xamarin** para criar essas experiências.

-   Comece com [Configuração e instalação](../cross-platform/setup-and-install.md), um processo que levará um tempo (normalmente 2 a 4 horas dependendo da velocidade da sua conexão de Internet, o que você já instalou e as opções selecionadas).

-   Enquanto os instaladores estão em execução, você pode [Saber mais sobre desenvolvimento móvel com Xamarin](learn-about-mobile-development-with-xamarin.md), que informa a natureza do Xamarin, compara o Xamarin.Forms a interface do usuário nativa e muito mais.

-   Depois que a instalação for concluída, [Verifique seu ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md).

-   Conclua ao passar pelo tutorial [Aprendendo as noções básicas de build de aplicativos com o Xamarin.Forms no Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

É possível trabalhar com todos os recursos do Xamarin usando [qualquer edição do Visual Studio 2017](https://visualstudio.microsoft.com/vs) (Community, Professional e Enterprise). Não é necessária nenhuma licença separada.

> [!NOTE]
>  Essas instruções descrevem a configuração de computador mais fácil e simples para desenvolvedores com experiência em Windows e Visual Studio. Com essa configuração, a experiência de desenvolvimento geral é simplificada porque basta precisa interagir com o Mac para usar o simulador do iOS e dispositivos vinculados. Se você tem experiência com Mac, execute o Visual Studio no Parallels ou no VMWare ou use o Visual Studio para Mac. Consulte [Configuração, instalação e verificações para usuários do Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md) Microsoft Docs.

> [!NOTE]
>  Caso esteja procurando uma solução de desenvolvimento multiplataforma baseada em HTML e CSS, confira as Ferramentas para Apache Cordova do Visual Studio, conforme descrito em [Desenvolvimento multiplataforma no Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).