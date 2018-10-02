---
title: 'Como: definir a publicação do ClickOnce versão | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: d832f28ddbd12bd72d018c841cf114ddae709e38
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475047"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Como definir a versão da publicação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: definir a versão de publicação do ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-set-the-clickonce-publish-version).  
  
O [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` propriedade determina se o aplicativo que você está publicando será tratado como uma atualização. É incrementado a cada versão do tempo, o aplicativo será publicado como uma atualização.  
  
 O `Publish Version` propriedade pode ser definida na **Publish** página da **Designer de projeto**.  
  
> [!NOTE]
>  Há uma opção de projeto automaticamente incrementará o `Publish Version` propriedade cada vez que o aplicativo é publicado; essa opção é habilitada por padrão. Para obter mais informações, consulte [como: incrementar automaticamente a versão de publicação do ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Para alterar a versão de publicação  
  
1.  Com um projeto selecionado no **Gerenciador de soluções**diante a **Project** menu, clique em **propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **Publish Version** campo, incremente o **principais**, **secundárias**, **Build**, ou **revisão** versão números.  
  
    > [!NOTE]
    >  Você nunca deve diminuir um número de versão; Isso pode gerar comportamento de atualização imprevisíveis.  
  
## <a name="see-also"></a>Consulte também  
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Como incrementar automaticamente a versão de publicação do ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



