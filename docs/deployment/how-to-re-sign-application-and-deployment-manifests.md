---
title: "Como: assinar novamente os manifestos de aplicativo e implantação | Microsoft Docs"
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
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: baa3e9310946482a4c7c64fdb619ce612a21dbda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Como assinar manifestos de aplicativo e implantação novamente
Depois de fazer alterações às propriedades de implantação no manifesto do aplicativo para aplicativos de formulários do Windows, os aplicativos do Windows Presentation Foundation (xbap) ou soluções do Office, você deve assinar novamente o aplicativo e manifestos de implantação com um certificado. Esse processo garante que arquivos violados não estão instalados nos computadores dos usuários finais.  
  
 Outro cenário em que você pode assinar novamente os manifestos é quando os clientes desejam assinar o aplicativo e manifestos de implantação com seu próprio certificado.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Manifestos de assinar novamente o aplicativo e implantação  
 Este procedimento pressupõe que você já fez alterações para o arquivo de manifesto do aplicativo (. manifest). Para obter mais informações, consulte [como: alterar propriedades de implantação](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para assinar novamente o aplicativo e implantação manifestos com Mage.exe  
  
1.  Abra um **Prompt de comando do Visual Studio** janela.  
  
2.  Altere os diretórios para a pasta que contém os arquivos de manifesto que você deseja assinar.  
  
3.  Digite o comando a seguir para assinar o arquivo de manifesto de aplicativo. Substitua ManifestFileName com o nome do arquivo de manifesto mais a extensão. Substitua o certificado com o caminho totalmente qualificado ou relativo do arquivo do certificado e senha com a senha do certificado.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para assinar um manifesto de aplicativo para um suplemento, um aplicativo de formulário do Windows ou um aplicativo de navegador do Windows Presentation Foundation. Certificados temporários criados pelo Visual Studio não são recomendados para implantação em ambientes de produção.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Digite o seguinte comando para atualizar e assinar o arquivo de manifesto de implantação, substituindo os nomes de espaço reservado como na etapa anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para atualizar e assinar um manifesto de implantação para um suplemento do Excel, um aplicativo Windows Forms ou um aplicativo de navegador do Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Opcionalmente, copie o manifesto de implantação mestre (publicar\\*appname*. Application) para o diretório de implantação da versão (arquivos publish\Application\\*appname*_ *versão*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Atualizando e assinar novamente os manifestos de aplicativo e implantação  
 Este procedimento pressupõe que você já fez alterações no seu aplicativo (. manifest) do arquivo de manifesto, mas que há outros arquivos que foram atualizados. Quando arquivos são atualizados, o hash que representa o arquivo também deve ser atualizado.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para atualizar e assinar novamente o aplicativo e implantação manifestos com Mage.exe  
  
1.  Abra um **Prompt de comando do Visual Studio** janela.  
  
2.  Altere os diretórios para a pasta que contém os arquivos de manifesto que você deseja assinar.  
  
3.  Remova a extensão de arquivo. Deploy dos arquivos na pasta de saída de publicação.  
  
4.  Digite o seguinte comando para atualizar o manifesto do aplicativo com os hashes de novo para os arquivos atualizados e assinar o arquivo de manifesto do aplicativo. Substitua ManifestFileName com o nome do arquivo de manifesto mais a extensão. Substitua o certificado com o caminho totalmente qualificado ou relativo do arquivo do certificado e senha com a senha do certificado.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para assinar um manifesto de aplicativo para um suplemento, um aplicativo de formulário do Windows ou um aplicativo de navegador do Windows Presentation Foundation. Certificados temporários criados pelo Visual Studio não são recomendados para implantação em ambientes de produção.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Digite o seguinte comando para atualizar e assinar o arquivo de manifesto de implantação, substituindo os nomes de espaço reservado como na etapa anterior.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para atualizar e assinar um manifesto de implantação para um suplemento do Excel, um aplicativo Windows Forms ou um aplicativo de navegador do Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Adicione a extensão de arquivo. Deploy para os arquivos, exceto os arquivos de manifesto de aplicativo e implantação.  
  
7.  Opcionalmente, copie o manifesto de implantação mestre (publicar\\*appname*. Application) para o diretório de implantação da versão (arquivos publish\Application\\*appname*_ *versão*).  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Como depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Como: adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Como configurar o comportamento do prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)