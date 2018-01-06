---
title: "Como: especificar uma URL de suporte para pré-requisitos individuais em uma implantação de ClickOnce | Microsoft Docs"
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
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 4a73d6cd0996f3f0e91b5a5381ee1b8ccd58a2a1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Como especificar uma URL de suporte para pré-requisitos individuais em uma implantação do ClickOnce
Um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação pode testar para um número de pré-requisitos que devem estar disponíveis no computador cliente para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo para ser executado. Isso inclui a versão mínima necessária do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], a versão do sistema operacional e todos os assemblies que devem ser instalados no cache de assembly global (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], no entanto, não é possível instalar qualquer um desses pré-requisitos em si; Se um pré-requisito não for encontrado, ele simplesmente interrompe a instalação e exibe uma caixa de diálogo explicando por que a instalação falhou.  
  
 Há dois métodos para instalar os pré-requisitos. Você pode instalá-los usando um aplicativo bootstrapper. Como alternativa, você pode especificar uma URL de suporte para pré-requisitos individuais, que é exibida aos usuários na caixa de diálogo se o pré-requisito não for encontrado. A página referenciada por essa URL pode conter links para instruções de instalação dos pré-requisitos necessários. Se um aplicativo não especificar uma URL de suporte para um pré-requisito individual, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exibe a URL de suporte especificada no manifesto de implantação para o aplicativo como um todo, se ele está definido.  
  
 Enquanto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe e MageUI.exe podem ser usadas para gerar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações, nenhuma dessas ferramentas oferece suporte direto ao especificar uma URL de suporte para pré-requisitos individuais. Este documento descreve como modificar sua implantação manifesto de aplicativo e o manifesto de implantação para incluir essas URLs de suporte.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Especificando uma URL de suporte para um pré-requisito individual  
  
1.  Abra o manifesto do aplicativo (o arquivo. manifest) para sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo em um editor de texto.  
  
2.  Um pré-requisito de sistema operacional, adicione o `supportUrl` de atributo para o `dependentOS` elemento:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Um pré-requisito para uma determinada versão do common language runtime, adicione o `supportUrl` de atributo para o `dependentAssembly` entrada que especifica a dependência de tempo de execução de linguagem comum:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Para um pré-requisito para um assembly que deve ser instalado no cache de assembly global, defina o `supportUrl` para o `dependentAssembly` elemento que especifica o assembly necessário:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Opcional. Para aplicativos voltados para o .NET Framework 4, abra o manifesto de implantação (o arquivo. Application) para sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo em um editor de texto.  
  
6.  Um pré-requisito do .NET Framework 4, adicione o `supportUrl` de atributo para o `compatibleFrameworks` elemento:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Depois que você alterou manualmente o manifesto do aplicativo, você deve assinar novamente o manifesto do aplicativo usando o certificado digital, em seguida, atualizar e assinar novamente o manifesto de implantação. Você deve usar o Mage.exe ou MageUI.exe SDK ferramentas para realizar essa tarefa, como regenerar esses arquivos usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] apaga as alterações manuais. Para obter mais informações sobre como usar Mage.exe para assinar novamente os manifestos, consulte [como: assinar novamente os manifestos de aplicativo e implantação](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 A URL de suporte não é exibida na caixa de diálogo se o aplicativo está marcado para ser executado em confiança parcial.  
  
## <a name="see-also"></a>Consulte também  
 [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)  (Instruções passo a passo: implantando manualmente um aplicativo ClickOnce)  
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Pré-requisitos de implantação de aplicativos](../deployment/application-deployment-prerequisites.md)