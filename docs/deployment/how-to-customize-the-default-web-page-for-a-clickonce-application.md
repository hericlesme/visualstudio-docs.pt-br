---
title: 'Como: personalizar a página da Web padrão para um aplicativo ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 743d7f259da4129eda578808d1ce04619104a3f1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Como personalizar a página da Web padrão para um aplicativo ClickOnce
Ao publicar um aplicativo ClickOnce para a Web, uma página da Web é gerada automaticamente e publicada juntamente com o aplicativo. A página padrão contém o nome do aplicativo e links para instalar o aplicativo, instale os pré-requisitos ou acessar a Ajuda no MSDN.  
  
> [!NOTE]
>  Os links reais que você vê na página dependem do computador em que a página está sendo exibida e o que você está incluindo de pré-requisitos.  
  
 O nome padrão para a página da Web é Publish; Você pode alterar o nome no **Project Designer**. Para obter mais informações, consulte [como: especificar uma página de publicação para um aplicativo ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 A página da Publish.htm Web é publicada somente se for detectada uma versão mais recente.  
  
> [!NOTE]
>  As alterações feitas à sua **publicar** configurações não afetarão a página Publish, com uma exceção: se você adicionar ou remove pré-requisitos depois de publicar inicialmente, a lista de pré-requisitos não serão precisa. Você precisará editar o texto do link de pré-requisito refletir as alterações.  
  
### <a name="to-customize-the-publish-web-page"></a>Para personalizar a página da Web de publicação  
  
1.  Publica seu aplicativo ClickOnce para um local da Web. Para obter mais informações, consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  No servidor Web, abra o arquivo Publish no Visual Web Designer ou outro editor de HTML.  
  
3.  Personalizar a página conforme desejado e salve-o.  
  
4.  Opcional. Para impedir que o Visual Studio substituindo sua página da Web de publicação personalizada, desmarque a opção **gerar automaticamente a página da web de implantação depois de cada publicação** na caixa de diálogo Opções de publicação.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Como especificar uma página de publicação para um aplicativo ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)