---
title: "Como: desabilitar a ativação de URL de aplicativos ClickOnce | Microsoft Docs"
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
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1142a047dc1e3ad74b75cf2d82432e1d2f16c1a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Como desabilitar a ativação de aplicativos ClickOnce pela URL
Normalmente, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será iniciado automaticamente imediatamente após a instalação de um servidor Web. Por motivos de segurança, você pode decidir desativar esse comportamento e diga aos usuários para iniciar o aplicativo a partir de **iniciar** menu em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.  
  
 Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalados no computador do usuário de um servidor Web. Ele não pode ser usado para aplicativos somente online, que podem ser iniciados apenas por meio de sua URL. Para obter mais informações sobre a diferença entre os aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimento usa o [! INCLUIR[winsdklong](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Você também pode executar esse procedimento usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para o seu aplicativo  
  
1.  Abra o manifesto de implantação no MageUI.exe. Se você ainda não tiver criado uma, siga as etapas em [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Selecione o **opções de implantação** guia.  
  
3.  Limpar o **executar o aplicativo após a instalação automaticamente** caixa de seleção.  
  
4.  Salve e assinar o manifesto.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)