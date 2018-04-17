---
title: Concedendo confiança a soluções do Office | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d3e89f9d864e80c3f3343b0d352105365e95e82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="granting-trust-to-office-solutions"></a>Concedendo confiança a soluções do Office
  Concedendo confiança a soluções do Office significa a modificação da política de segurança de cada computador de destino para o conjunto de solução, o manifesto do aplicativo, o manifesto de implantação e documento de confiança. Relação de confiança pode ser concedida para a solução do Office por você ou o usuário final.  
  
 Você pode conceder confiança total para a solução do Office ao assinar os manifestos de aplicativo e implantação.  
  
 Os usuários finais podem conceder confiança para a solução do Office fazendo uma decisão de confiança no [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt confiável.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Manifestos de confiança a solução ao assinar o aplicativo e implantação  
 Manifestos de todos os aplicativos e implantação para o Office solutions devem ser assinados com um certificado que identifica o Editor. Os certificados fornecem uma base para tomar decisões de confiança.  
  
 Um certificado temporário é criado para você e receber confiança no momento da compilação para a solução seja executada enquanto você depurá-lo. Se você publicar uma solução que está assinada com um certificado temporário, o usuário final será solicitado a tomar uma decisão de confiança.  
  
 Se você se conectar a solução com um certificado conhecido e confiável, a solução será instalada automaticamente sem avisar o usuário final para tomar uma decisão de confiança. Para obter mais informações sobre como obter um certificado para assinar, consulte [ClickOnce e Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Depois de obter um certificado, o certificado deve ser explicitamente confiável adicionando-o à lista de editores confiáveis. Para obter mais informações, consulte [como: adicionar um editor confiável para um computador cliente para aplicativos ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Se um desenvolvedor fizer a solução com um certificado temporário, um administrador pode assinar novamente a personalização com um certificado conhecido e confiável, usando a ferramenta de edição (mage.exe), que é uma das ferramentas do Microsoft .NET Framework e geração de manifesto. Para obter mais informações sobre como assinar soluções, consulte [como: soluções do Office sinal](../vsto/how-to-sign-office-solutions.md) e [como: entrada manifestos de aplicativo e implantação](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a> Confiando a solução usando o Prompt confiável do ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] solicita ao usuário final para tomar a decisão de confiança, se não houver nenhuma política de toda a organização confiança do certificado da solução. Se o usuário final concede confiança para a solução, uma entrada da lista de inclusão é criada que contém uma URL e uma chave pública para armazenar a decisão de confiança. Quando uma personalização confiável é executada mais tarde, o usuário final não é solicitado novamente.  
  
 Os administradores podem desabilitar o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt confiável ou exigem que o prompt ocorrer apenas para as soluções são assinadas com um certificado Authenticode. Para obter mais informações sobre como alterar essas configurações para as zonas MyComputer, LocalIntranet, Internet, TrustedSites e UntrustedSites, consulte [como: configurar o comportamento do Prompt de confiança ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)   
 [Concedendo confiança a documentos](../vsto/granting-trust-to-documents.md)   
 [Solucionando problemas de segurança de solução do Office](../vsto/troubleshooting-office-solution-security.md)   
 [Considerações sobre segurança específicas para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  