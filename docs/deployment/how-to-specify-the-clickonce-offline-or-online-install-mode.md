---
title: 'Como: especificar o ClickOnce Offline ou instalar o modo Online | Microsoft Docs'
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b1c0f8615513639081351bdf77ea9ec63fc8309b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Como especificar o modo de instalação offline ou online do ClickOnce
O `Install Mode` para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo determina se o aplicativo estará disponível offline ou online. Quando você escolhe **o aplicativo está disponível apenas online**, o usuário deve ter acesso para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] local (uma página da Web ou um compartilhamento de arquivos) para executar o aplicativo de publicação. Quando você escolhe **o aplicativo está disponível também offline**, o aplicativo adiciona entradas para o **iniciar** menu e **adicionar ou remover programas** caixa de diálogo; o usuário é é possível executar o aplicativo quando não estão conectados.  
  
 O `Install Mode` pode ser definido na **publicar** página do **Project Designer**.  
  
 **Observação** o `Install Mode` também podem ser definidas usando o Assistente de publicação. Para obter mais informações, consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Para disponibilizar um aplicativo ClickOnce online apenas  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **configurações e instalar o modo** área, clique no **o aplicativo está disponível apenas online** botão de opção.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Para disponibilizar um aplicativo ClickOnce online ou offline  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **configurações e instalar o modo** área, clique no **o aplicativo está disponível também offline** botão de opção.  
  
     Quando instalado, o aplicativo adiciona entradas para o **iniciar** menu e **adicionar ou remover programas** no painel de controle.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um Aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)