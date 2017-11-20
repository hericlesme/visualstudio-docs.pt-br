---
title: "Como: habilitar o AutoStart para instalações do CD | Microsoft Docs"
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
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: e3656c3d32dcba946cf66d7fba56a68b3de467f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Como habilitar o AutoStart para instalações por CD
Ao implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo por meio de uma mídia removível, como CD-ROM ou DVD-ROM, você pode habilitar `AutoStart` para que o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é iniciado automaticamente quando a mídia for inserida.  
  
 `AutoStart`pode ser habilitada no **publicar** página do **Project Designer**.  
  
### <a name="to-enable-autostart"></a>Para habilitar o AutoStart  
  
1.  Com um projeto selecionado no **Solution Explorer**, no **projeto** menu clique **propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **opções** botão.  
  
     O **opções de publicação** caixa de diálogo é exibida.  
  
4.  Clique em **implantação**.  
  
5.  Selecione o **instalações do CD para iniciar o Setup automaticamente quando o CD é inserido** caixa de seleção.  
  
     Um arquivo Autorun será copiado para o local de publicação quando o aplicativo é publicado.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)