---
title: 'Como: especificar o ClickOnce Offline ou Online de modo de instalação | Microsoft Docs'
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7f277966070e142ebc24d70acfcf4bf5502f419a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465444"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Como especificar o modo de instalação offline ou online do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: especificar o ClickOnce Offline ou Online instalar no modo](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-the-clickonce-offline-or-online-install-mode).  
  
O `Install Mode` para um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo determina se o aplicativo estará disponível offline ou online. Quando você escolhe **o aplicativo está disponível somente online**, o usuário deve ter acesso para o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] local (uma página da Web ou um compartilhamento de arquivos) para executar o aplicativo de publicação. Quando você escolhe **o aplicativo está disponível também offline**, o aplicativo adiciona entradas para o **inicie** menu e o **adicionar ou remover programas** caixa de diálogo; o usuário é é possível executar o aplicativo quando eles não estão conectados.  
  
 O `Install Mode` podem ser definidos na **Publish** página da **Designer de projeto**.  
  
 **Observação** o `Install Mode` também podem ser definidas usando o Assistente de publicação. Para obter mais informações, consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Para disponibilizar um aplicativo ClickOnce online apenas  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **modo de instalação e as configurações** área, clique no **o aplicativo está disponível apenas online** botão de opção.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Para disponibilizar um aplicativo ClickOnce online ou offline  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **modo de instalação e as configurações** área, clique no **o aplicativo está disponível também offline** botão de opção.  
  
     Quando instalado, o aplicativo adiciona entradas para o **inicie** menu e, ao **adicionar ou remover programas** no painel de controle.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um Aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



