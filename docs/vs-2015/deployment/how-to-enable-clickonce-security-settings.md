---
title: 'Como: Habilitar configurações de segurança do ClickOnce | Microsoft Docs'
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
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 65cba913afdee2379e5f702dda460cea2a33598f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462692"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Como habilitar configurações de segurança do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: Habilitar configurações de segurança do ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings).  
  
Segurança de acesso do código para aplicativos ClickOnce deve ser habilitada para publicar o aplicativo. Isso é feito automaticamente quando você publica um aplicativo usando o Assistente de publicação.  
  
 Em alguns casos, habilitar a segurança de acesso do código pode afetar o desempenho ao compilar ou depurar seu aplicativo. Nesses casos, convém desabilitar temporariamente as configurações de segurança.  
  
 Configurações de segurança do ClickOnce podem ser habilitadas ou desabilitadas na **segurança** página do **Designer de projeto**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Para habilitar as configurações de segurança do ClickOnce  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique na guia **Segurança**.  
  
3.  Selecione o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.  
  
     Agora você pode personalizar as configurações de segurança para seu aplicativo na página de segurança.  
  
    > [!NOTE]
    >  Essa caixa de seleção é selecionada automaticamente cada vez que o aplicativo é publicado com o **publicar** assistente.  
  
### <a name="to-disable-clickonce-security-settings"></a>Para desabilitar as configurações de segurança do ClickOnce  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique na guia **Segurança**.  
  
3.  Desmarque a **Habilitar configurações de segurança do ClickOnce** caixa de seleção.  
  
     O aplicativo será executado com as configurações de segurança de confiança total; todas as configurações de **segurança** página será ignorada.  
  
    > [!NOTE]
    >  Cada vez que o aplicativo é publicado com o Assistente de publicação, essa caixa de seleção será selecionada; Você deverá desmarcá-la novamente depois de cada publicação bem-sucedida.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)



