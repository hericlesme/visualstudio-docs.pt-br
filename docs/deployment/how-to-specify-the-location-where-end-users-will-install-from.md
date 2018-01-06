---
title: "Como: especificar o local onde os usuários finais instalarão de | Microsoft Docs"
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
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a3a2770933f4a9f600b12a2d601deca855de3a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Como especificar o local de onde os usuários finais instalarão
Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, o local onde os usuários estão para baixar e instalar o aplicativo não é necessariamente o local onde você publica o aplicativo inicialmente. Por exemplo, em algumas organizações, um desenvolvedor pode publicar um aplicativo para um servidor de preparo e, em seguida, um administrador deve mover o aplicativo em um servidor Web.  
  
 Nesse caso, você pode usar o `Installation URL` propriedade para especificar o servidor Web onde os usuários irão fazer download do aplicativo. Isso é necessário para que o manifesto do aplicativo saiba onde procurar atualizações.  
  
 O `Installation URL` propriedade pode ser definida no **publicar** página do **Project Designer**.  
  
 **Observação** o `Installation URL` propriedade também pode ser definida usando o **PublishWizard**. Para obter mais informações, consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Para especificar uma URL de instalação  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No campo URL de instalação, digite o local de instalação usando uma URL totalmente qualificada usando o formato http://www.microsoft.com/ApplicationName ou um caminho UNC no formato \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Consulte também  
 [Como especificar o local em que o Visual Studio copiará os arquivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)