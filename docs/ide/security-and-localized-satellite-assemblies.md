---
title: "Assemblies satélite de segurança e localizados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 54c224b4c830f76c532b268b1e6afe17013ab6c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-localized-satellite-assemblies"></a>Assemblies satélite de segurança e localizados
Se seu assembly principal usar nomenclatura forte, assemblies satélites deverão ser assinados com a mesma chave privada que o assembly principal. Se o par de chave pública/privada não corresponder entre os assemblies satélites e principal, seus recursos não serão carregados. Para obter mais informações sobre a assinatura de assemblies, consulte [Como assinar um assembly com um nome forte](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 Em geral, você poderá precisar que o grupo de assinatura da sua organização ou uma organização de assinatura externa assine com a chave privada. Isso ocorre devido à natureza confidencial da chave privada: o acesso geralmente é limitado a algumas pessoas. Você pode usar assinatura atrasada durante o desenvolvimento. Para obter mais informações, consulte [Assinando um assembly com atraso](/dotnet/framework/app-domains/delay-sign-assembly).  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança de assembly](/dotnet/framework/app-domains/assembly-security-considerations)   
 [Principais conceitos de segurança](/dotnet/standard/security/key-security-concepts)   
 [Introdução a aplicativos internacionais com base no .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Localizando aplicativos](../ide/localizing-applications.md)   
 [Globalizando e localizando aplicativos](../ide/globalizing-and-localizing-applications.md)