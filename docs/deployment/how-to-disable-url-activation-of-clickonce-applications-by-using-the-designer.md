---
title: "Como: desabilitar a ativação de URL de aplicativos ClickOnce usando o Designer | Microsoft Docs"
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
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d4df4bab3b3dd7ed29dd3e5d3ca2ff7e56c1922d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Como desabilitar a ativação de aplicativos ClickOnce pela URL usando o designer
Normalmente, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será iniciado automaticamente imediatamente após a instalação de um servidor Web. Por motivos de segurança, você pode decidir desativar esse comportamento e diga aos usuários para iniciar o aplicativo a partir de **iniciar** menu em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.  
  
 Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalados no computador do usuário de um servidor Web. Ele não pode ser usado para aplicativos somente online, que podem ser iniciados apenas por meio de sua URL. Para obter mais informações sobre a diferença entre os aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimento usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você também pode realizar essa tarefa usando o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obter mais informações, consulte [como: desabilitar a ativação de URL de aplicativos ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para o seu aplicativo  
  
1.  Clique o nome do projeto em **Solution Explorer**e clique em **propriedades**.  
  
2.  Sobre o **propriedades** , clique no **publicar** guia.  
  
3.  Clique em **opções**.  
  
4.  Clique em **manifestos**.  
  
5.  Selecione a caixa de seleção **bloqueia o aplicativo seja ativado através de uma URL**.  
  
6.  Implantar seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)