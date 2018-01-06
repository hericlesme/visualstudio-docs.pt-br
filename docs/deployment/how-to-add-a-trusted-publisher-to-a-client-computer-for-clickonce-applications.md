---
title: "Como: adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce | Microsoft Docs"
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
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 758bf6b7b12d8c32a1985b5c07ba5c66f3937415
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Como adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce
Com a implantação de aplicativos confiáveis, você pode configurar computadores cliente para que seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos executados com um nível mais alto de confiança sem avisar o usuário. Os procedimentos a seguir mostram como usar a ferramenta de linha de comando CertMgr.exe para adicionar um certificado de editor para o repositório de editores confiáveis em um computador cliente.  
  
 Os comandos que você usar variam ligeiramente, dependendo se a autoridade de certificação (CA) que emitiu o certificado faz parte de raiz confiável do cliente. Se um computador cliente do Windows for parte de um domínio, ele conterá, na lista de autoridades de certificação que são considerados confiáveis. Essa lista é geralmente configurada pelo administrador do sistema. Se seu certificado foi emitido por um essas raízes confiáveis, ou por uma autoridade de certificação que se conecte a um desses raízes confiáveis, você pode adicionar o certificado ao repositório de raiz confiável do cliente. Se, por outro lado, o certificado não foi emitido por uma dessas raízes confiáveis, você deve adicionar o certificado ao armazenamento raiz confiável do cliente e o repositório de editores confiáveis.  
  
> [!NOTE]
>  Você deve adicionar certificados dessa maneira em cada computador cliente para o qual você planeja implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que requer permissões elevadas. Você adicionar os certificados manualmente ou por meio de um aplicativo que você implantar em seus clientes. Você precisa configurar esses computadores de uma vez, após o qual você pode implantar qualquer número de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos assinados com o mesmo certificado.  
  
 Você também pode adicionar um certificado a um repositório programaticamente usando o <xref:System.Security.Cryptography.X509Certificates.X509Store> classe.  
  
 Para obter uma visão geral da implantação de aplicativos confiáveis, consulte [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Para adicionar um certificado para o repositório de editores confiáveis sob a raiz confiável  
  
1.  Obter um certificado digital de uma autoridade de certificação.  
  
2.  Exporte o certificado no formato Base64 x. 509 (. cer). Para obter mais informações sobre os formatos de certificado, consulte [exportar um certificado](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  No prompt de comando nos computadores cliente, execute o seguinte comando:  
  
     **certmgr.exe-adicionar chaves públicas - c -s - r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Para adicionar um certificado ao repositório de editores confiáveis em uma raiz diferente  
  
1.  Obter um certificado digital de uma autoridade de certificação.  
  
2.  Exporte o certificado no formato Base64 x. 509 (. cer). Para obter mais informações sobre os formatos de certificado, consulte [exportar um certificado](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  No prompt de comando nos computadores cliente, execute o seguinte comando:  
  
     **certmgr.exe-adicionar good.cer - c -s - r localMachine raiz**  
  
     **certmgr.exe-adicionar good.cer - c -s - r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Consulte também  
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)  (Instruções passo a passo: implantando manualmente um aplicativo ClickOnce)  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Como depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Como: adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Como: assinar novamente os manifestos de aplicativo e implantação](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Como configurar o comportamento do prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)