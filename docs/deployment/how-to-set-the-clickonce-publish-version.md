---
title: "Como: definir o ClickOnce publicação versão | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: db6bfae35bbbd14190028fb0e32dfc8d35cb9bac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Como definir a versão da publicação do ClickOnce
O [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` propriedade determina se o aplicativo que você está publicando será tratado como uma atualização. Cada versão de tempo é incrementado, o aplicativo será publicado como uma atualização.  
  
 O `Publish Version` propriedade pode ser definida no **publicar** página do **Project Designer**.  
  
> [!NOTE]
>  Há uma opção de projeto será incrementado automaticamente o `Publish Version` propriedade sempre que o aplicativo é publicado; essa opção é habilitada por padrão. Para obter mais informações, consulte [como: automaticamente incrementar a versão de publicação do ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Para alterar a versão de publicação  
  
1.  Com um projeto selecionado no **Solution Explorer**, no **projeto** menu clique **propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Em **versão publicar** campo, incrementar o **principais**, **secundária**, **criar**, ou **revisão** versão números.  
  
    > [!NOTE]
    >  Você nunca deve diminuir um número de versão; Isso pode causar comportamento imprevisível atualização.  
  
## <a name="see-also"></a>Consulte também  
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Como incrementar automaticamente a versão de publicação do ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)