---
title: "Como: Ativar configurações de segurança do ClickOnce | Microsoft Docs"
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
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d9fb07f8348e161743b373a83d49c4dd614d8c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-clickonce-security-settings"></a>Como habilitar configurações de segurança do ClickOnce
Segurança de acesso ao código para aplicativos ClickOnce deve ser habilitada para publicar o aplicativo. Isso é feito automaticamente quando você publica um aplicativo usando o Assistente de publicação.  
  
 Em alguns casos, habilitando a segurança de acesso de código pode afetar o desempenho quando compilar ou depurar seu aplicativo. Nesses casos, talvez você queira desabilitar temporariamente as configurações de segurança.  
  
 Configurações de segurança do ClickOnce podem ser habilitadas ou desabilitadas a **segurança** página do **Project Designer**.  
  
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
  
3.  Limpar o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.  
  
     O aplicativo será executado com as configurações de segurança de confiança total; todas as configurações do **segurança** página será ignorada.  
  
    > [!NOTE]
    >  Cada vez que o aplicativo é publicado com o Assistente de publicação, essa caixa de seleção será selecionada; é necessário desmarcá-la novamente depois de cada publicação bem-sucedida.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 
