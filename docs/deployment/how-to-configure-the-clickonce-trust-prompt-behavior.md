---
title: 'Como: configurar o comportamento do Prompt confiável do ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d37e5fa465a5e19b1bfb7577f6ab06c61782f775
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561549"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Como configurar o comportamento do prompt confiável do ClickOnce
Você pode configurar o prompt de confiança do ClickOnce para controlar se os usuários finais recebem a opção de instalação de aplicativos ClickOnce, como aplicativos do Windows Forms, aplicativos do Windows Presentation Foundation, aplicativos de console, navegador WPF os aplicativos e soluções do Office. Configurar o prompt de confiança, definindo as chaves do registro no computador de cada usuário final.  
  
 A tabela a seguir mostra as opções de configuração que podem ser aplicadas a cada uma das cinco zonas (Internet, UntrustedSites, MyComputer, LocalIntranet e TrustedSites).  
  
|Opção|Valor de configuração do registro|Descrição|  
|------------|----------------------------|-----------------|  
|Habilite o prompt de confiança.|`Enabled`|O prompt de relação de confiança de ClickOnce é a exibição para que os usuários finais podem conceder a relação de confiança para aplicativos ClickOnce.|  
|Restringir o prompt de confiança.|`AuthenticodeRequired`|Prompt de relação de confiança de ClickOnce é exibido apenas se os aplicativos ClickOnce são assinados com um certificado que identifica o Editor.|  
|Desabilite o prompt de confiança.|`Disabled`|O prompt de confiança do ClickOnce não é exibido para todos os aplicativos ClickOnce que não são assinados com um certificado confiável explicitamente.|  
  
 A tabela a seguir mostra o comportamento padrão para cada zona. A coluna de aplicativos se refere a aplicativos de Windows Forms, aplicativos do Windows Presentation Foundation, aplicativos de navegador WPF e aplicativos de console.  
  
|Zona|Aplicativos|Soluções do Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Você pode substituir essas configurações, permitindo, restringindo ou desabilitar o prompt de confiança do ClickOnce.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Habilitando o Prompt confiável do ClickOnce  
 Habilite o prompt de confiança para uma zona quando desejar que os usuários finais devem ser apresentados com a opção de instalação e execução de qualquer aplicativo ClickOnce que vêm de zona.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para habilitar o prompt de confiança do ClickOnce usando o editor do registro  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **iniciar**e, em seguida, clique em **executar**.  
  
    2.  No **abrir** , digite `regedit32`e, em seguida, clique em **Okey**.  
  
2.  Localize a seguinte chave do registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se a chave não existir, crie-o.  
  
3.  Adicione as seguintes subchaves como **valor de cadeia de caracteres**, se ainda não existirem, com os valores associados mostrados na tabela a seguir.  
  
    |Subchave do valor de cadeia de caracteres|Valor|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Para soluções do Office, `Internet` tem o valor padrão `AuthenticodeRequired` e `UntrustedSites` tem o valor `Disabled`. Todas as outras pessoas, `Internet` tem o valor padrão `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Para habilitar o prompt de confiança do ClickOnce programaticamente  
  
1.  Crie um aplicativo de console do Visual Basic ou Visual c# no Visual Studio.  
  
2.  Abra o arquivo vb ou Program.cs para edição e adicione o código a seguir.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Crie e execute o aplicativo.  
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Restringindo o Prompt confiável do ClickOnce  
 Restringir o prompt confiável para que soluções devem ser assinadas com certificados Authenticode conhecidos identidade antes dos usuários são solicitados para uma decisão de confiança.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para restringir o prompt de confiança do ClickOnce usando o editor do registro  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **iniciar**e, em seguida, clique em **executar**.  
  
    2.  No **abrir** , digite `regedit`e, em seguida, clique em **Okey**.  
  
2.  Localize a seguinte chave do registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se a chave não existir, crie-o.  
  
3.  Adicione as seguintes subchaves como **valor de cadeia de caracteres**, se ainda não existirem, com os valores associados mostrados na tabela a seguir.  
  
    |Subchave do valor de cadeia de caracteres|Valor|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Para restringir o prompt de confiança do ClickOnce programaticamente  
  
1.  Crie um aplicativo de console do Visual Basic ou Visual c# no Visual Studio.  
  
2.  Abra o arquivo vb ou Program.cs para edição e adicione o código a seguir.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Crie e execute o aplicativo.  
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Desabilitando o Prompt confiável do ClickOnce  
 Você pode desabilitar o prompt de confiança para que os usuários finais não recebem a opção de instalar as soluções que já não são confiáveis em sua política de segurança.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para desativar o prompt de confiança do ClickOnce usando o editor do registro  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **iniciar**e, em seguida, clique em **executar**.  
  
    2.  No **abrir** , digite `regedit`e, em seguida, clique em **Okey**.  
  
2.  Localize a seguinte chave do registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se a chave não existir, crie-o.  
  
3.  Adicione as seguintes subchaves como **valor de cadeia de caracteres**, se ainda não existirem, com os valores associados mostrados na tabela a seguir.  
  
    |Subchave do valor de cadeia de caracteres|Valor|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Para desativar o prompt de confiança do ClickOnce programaticamente  
  
1.  Crie um aplicativo de console do Visual Basic ou Visual c# no Visual Studio.  
  
2.  Abra o arquivo vb ou Program.cs para edição e adicione o código a seguir.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Crie e execute o aplicativo.  
  
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
 [Como assinar manifestos de aplicativo e implantação novamente](../deployment/how-to-re-sign-application-and-deployment-manifests.md)