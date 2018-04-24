---
title: 'Como: especificar uma página de publicação para um aplicativo ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 864d0ef0f4934e040722a9a9fc00ba7a54f3331c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
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