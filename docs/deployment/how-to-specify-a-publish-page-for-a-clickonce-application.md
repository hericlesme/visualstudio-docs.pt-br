---
title: "Como: especificar uma página de publicação para um aplicativo ClickOnce | Microsoft Docs"
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: e05718d2a00df76d2c78e16c5b4473ab48d43a39
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Como especificar uma página de publicação para um aplicativo ClickOnce
Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, uma página de Web padrão (Publish) é gerada e publicada juntamente com o aplicativo. Esta página contém o nome do aplicativo, um link para instalar o aplicativo e/ou em todos os pré-requisitos e um link para um tópico da Ajuda que descreve [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. O **publicar página** propriedade para o seu projeto permite que você especifique um nome para a página da Web para sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
 Depois que a página de publicação tiver sido especificada, na próxima vez que você publicar, ele será copiado para o local de publicação; ele não será substituído se você publicar novamente. Se você deseja personalizar a aparência da página, você pode fazer isso sem se preocupar com a perda das alterações. Para obter mais informações, consulte [como: personalizar a página de Web padrão do ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 O **publicar página** propriedade pode ser definida **opções de publicação** caixa de diálogo, acessível a partir de **publicar** painel do **Project Designer**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Para especificar uma página da Web personalizada para um aplicativo ClickOnce  
  
1.  Com um projeto selecionado no **Solution Explorer**, no **projeto** menu clique **propriedades**.  
  
2.  Selecione o **publicar** painel.  
  
3.  Clique o **opções** para abrir o **opções de publicação** caixa de diálogo.  
  
4.  Clique em **implantação**.  
  
5.  No **opções de publicação** caixa de diálogo caixa, certifique-se de que o **página da web de implantação aberto depois de publicar** caixa de seleção estiver marcada (ele deve ser selecionado por padrão).  
  
6.  No **página da web de implantação:** caixa, digite o nome da página da Web e, em seguida, clique em **Okey**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Para impedir que a página de publicação iniciar cada vez que você publicar  
  
1.  Com um projeto selecionado no **Solution Explorer**, no **projeto** menu clique **propriedades**.  
  
2.  Selecione o **publicar** painel.  
  
3.  Clique o **opções** para abrir o **opções de publicação** caixa de diálogo.  
  
4.  Clique em **implantação**.  
  
5.  No **opções de publicação** caixa de diálogo, desmarque o **página da web de implantação aberto depois de publicar** caixa de seleção.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um Aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Como: personalizar a página da Web padrão do ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)