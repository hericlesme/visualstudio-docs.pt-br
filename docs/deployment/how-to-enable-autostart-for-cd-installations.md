---
title: 'Como: habilitar o AutoStart para instalações do CD | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 230f0491993b3804c3147e727900de2647ff7bda
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558237"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Como habilitar o AutoStart para instalações por CD
Ao implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo por meio de uma mídia removível, como CD-ROM ou DVD-ROM, você pode habilitar `AutoStart` para que o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é iniciado automaticamente quando a mídia for inserida.  
  
 `AutoStart` pode ser habilitada no **publicar** página do **Project Designer**.  
  
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