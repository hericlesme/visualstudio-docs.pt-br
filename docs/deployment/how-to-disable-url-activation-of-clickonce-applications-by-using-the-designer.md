---
title: 'Como: desabilitar a ativação de aplicativos ClickOnce pela URL usando o Designer | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97357dd92525be2d36b552c5f3df49080f46d29b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152027"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Como: desabilitar a ativação de aplicativos ClickOnce pela URL usando o Designer
Normalmente, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será iniciado automaticamente, imediatamente após a instalação de um servidor Web. Por motivos de segurança, você pode optar por desabilitar esse comportamento e diga aos usuários para iniciar o aplicativo a partir de **iniciar** menu em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.  
  
 Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalados no computador do usuário de um servidor Web. Ele não pode ser usado para aplicativos somente online, que podem ser iniciados apenas por meio de sua URL. Para obter mais informações sobre a diferença entre os aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimento usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você também pode realizar essa tarefa usando o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obter mais informações, consulte [como: desabilitar a ativação de URL de aplicativos ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para seu aplicativo  
  
1.  Nome do projeto no botão direito do mouse **Gerenciador de soluções**e clique em **propriedades**.  
  
2.  Sobre o **propriedades** , clique no **publicar** guia.  
  
3.  Clique em **opções**.  
  
4.  Clique em **manifestos**.  
  
5.  Selecione a caixa de seleção rotulada **bloquear o aplicativo seja ativado através de uma URL**.  
  
6.  Implantar seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)