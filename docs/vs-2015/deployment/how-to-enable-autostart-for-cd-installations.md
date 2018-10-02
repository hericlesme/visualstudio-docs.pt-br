---
title: 'Como: habilitar o AutoStart para instalações por CD | Microsoft Docs'
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
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7a0f7228e4340763104f38dc56e5e8603ed85408
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462360"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Como habilitar o AutoStart para instalações por CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: habilitar o AutoStart para instalações por CD](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-autostart-for-cd-installations).  
  
Ao implantar uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo por meio de uma mídia removível, como CD-ROM ou DVD-ROM, você pode habilitar `AutoStart` para que o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo seja iniciado automaticamente quando a mídia for inserida.  
  
 `AutoStart` pode ser habilitada na **Publish** página do **Designer de projeto**.  
  
### <a name="to-enable-autostart"></a>Para habilitar o AutoStart  
  
1.  Com um projeto selecionado no **Gerenciador de soluções**diante a **Project** menu, clique em **propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **opções** botão.  
  
     O **opções de publicação** caixa de diálogo é exibida.  
  
4.  Clique em **implantação**.  
  
5.  Selecione o **instalações para CD, iniciar automaticamente a instalação quando o CD é inserido** caixa de seleção.  
  
     Um arquivo Autorun será copiado para o local de publicação quando o aplicativo é publicado.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



