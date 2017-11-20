---
title: "Como: instalar pré-requisitos com um aplicativo ClickOnce | Microsoft Docs"
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
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 44acef520a15b86e15906eb4197f538b23b92d8a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Como instalar pré-requisitos com um aplicativo ClickOnce
Todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos exigem que a versão correta do .NET Framework é instalada em um computador antes de ser executados; muitos aplicativos têm também outros pré-requisitos. Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, você pode escolher um conjunto de componentes de pré-requisito para ser empacotado junto com seu aplicativo. No momento da instalação, uma verificação será executada para cada pré-requisito determinar se ele já existe; Se não for instalado antes de instalar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
 Em vez de empacotamento e pré-requisitos de publicação, você também pode especificar um local de download para os componentes. Por exemplo, em vez de incluir pré-requisitos com todos os aplicativos que você publicar, você pode usar um compartilhamento de arquivos centralizado ou o local da Web que contém os instaladores para todos os seus pré-requisitos — no momento da instalação, os componentes serão baixados e instalados a partir desse local.  
  
> [!IMPORTANT]
>  Você deve adicionar pacotes de instalador de pré-requisitos para seu computador de desenvolvimento antes de publicar seu primeiro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Para obter mais informações, consulte [como: incluir pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Pré-requisitos são gerenciadas no **pré-requisitos** caixa de diálogo, acessível a partir o **publicar** painel do **Project Designer**.  
  
> [!NOTE]
>  Além da lista predeterminada de pré-requisitos, você pode adicionar seus próprios componentes à lista. Para obter mais informações, consulte [criação de pacotes de Bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Para especificar os pré-requisitos para instalar com um aplicativo ClickOnce  
  
1.  Com um projeto selecionado no **Solution Explorer**, no **projeto** menu clique **propriedades**.  
  
2.  Selecione o **publicar** painel.  
  
3.  Clique o **pré-requisitos** para abrir o **pré-requisitos** caixa de diálogo.  
  
4.  Na caixa de diálogo **Pré-requisitos**, verifique se a caixa de seleção **Criar programa de instalação para instalar os componentes dos pré-requisitos** está marcada.  
  
5.  No **pré-requisitos** lista, verifique os componentes que você deseja instalar e, em seguida, clique em **Okey**.  
  
     Os componentes selecionados serão sejam empacotados e publicados juntamente com seu aplicativo.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Para especificar um local de download diferente pré-requisitos  
  
1.  Com um projeto selecionado no **Solution Explorer**, no **projeto** menu clique **propriedades**.  
  
2.  Selecione o **publicar** painel.  
  
3.  Clique o **pré-requisitos** para abrir o **pré-requisitos** caixa de diálogo.  
  
4.  Na caixa de diálogo **Pré-requisitos**, verifique se a caixa de seleção **Criar programa de instalação para instalar os componentes dos pré-requisitos** está marcada.  
  
5.  No **especificar o local de instalação de pré-requisitos** seção, selecione **baixar pré-requisitos no seguinte local**.  
  
6.  Selecione um local na lista suspensa, ou digite uma URL, o caminho do arquivo ou o local de FTP e, em seguida, clique em **Okey.**  
  
    > [!NOTE]
    >  Você deve certificar-se de que os instaladores para os componentes especificados existem no local especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)