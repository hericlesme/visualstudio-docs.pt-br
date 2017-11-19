---
title: "Como: configurar a segurança da lista de inclusão | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7032f3663be7df1a06fa4dc16d4f4473e4666cfc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-inclusion-list-security"></a>Como configurar a segurança da lista de inclusões
  Se você tiver permissões de administrador, você pode configurar o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt confiável para controlar se os usuários finais recebem a opção de instalação de soluções do Office, salvando uma decisão de confiança para a lista de inclusão. Para obter informações sobre listas de inclusão, consulte [confiar em soluções do Office por usando listas de inclusão](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para soluções que estão em cada um dos cinco zonas, você pode definir as seguintes opções:  
  
-   Habilitar o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiança Prompt chave e a lista de inclusão. Você pode permitir que os usuários finais conceder confiança a soluções do Office que são assinados com um certificado.  
  
-   Restringir o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiança Prompt chave e a lista de inclusão. Você pode permitir que os usuários finais instalar soluções do Office que são assinadas com um certificado que identifica o Editor, mas que ainda não for confiável.  
  
-   Desabilitar o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confiança Prompt chave e a lista de inclusão. Você pode impedir que os usuários finais instalar qualquer solução do Office que não está assinada com um certificado confiável explicitamente.  
  
## <a name="enabling-the-inclusion-list"></a>Habilitar a lista de inclusão  
 Habilite a lista de inclusão de uma zona quando desejar que os usuários finais devem ser apresentados com a opção de instalação e execução de qualquer solução do Office que vêm de zona.  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Para habilitar a lista de inclusão usando o editor do registro  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **iniciar**e, em seguida, clique em **executar**.  
  
    2.  No **abrir** , digite **regedt32.exe**e, em seguida, clique em **Okey**.  
  
2.  Localize a seguinte chave do registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se a chave não existir, crie-o.  
  
3.  Adicione as seguintes subchaves como **valor de cadeia de caracteres**, se ainda não existirem, com os valores associados.  
  
    |Subchave do valor de cadeia de caracteres|Valor|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Desabilitado**|  
    |**Meu computador**|**Habilitado**|  
    |**LocalIntranet**|**Habilitado**|  
    |**TrustedSites**|**Habilitado**|  
  
     Por padrão, **Internet** tem o valor **AuthenticodeRequired** e **UntrustedSites** tem o valor **desabilitado**.  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>Para habilitar a lista de inclusão programaticamente  
  
1.  Crie um aplicativo de console do Visual Basic ou Visual c#.  
  
2.  Abra o arquivo vb ou Program.cs para edição e adicione o código a seguir.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
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
  
## <a name="restricting-the-inclusion-list"></a>Restringir a lista de inclusão  
 Restringir a lista de inclusão para que as soluções devem ser assinadas com certificados Authenticode conhecidos identidade antes dos usuários são solicitados para uma decisão de confiança.  
  
#### <a name="to-restrict-the-inclusion-list"></a>Para restringir a lista de inclusão  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **iniciar**e, em seguida, clique em **executar**.  
  
    2.  No **abrir** , digite **regedt32.exe**e, em seguida, clique em **Okey**.  
  
2.  Localize a seguinte chave do registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se a chave não existir, crie-o.  
  
3.  Adicione as seguintes subchaves como **valor de cadeia de caracteres**, se ainda não existirem, com os valores associados.  
  
    |Subchave do valor de cadeia de caracteres|Valor|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Desabilitado**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Meu computador**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     Por padrão, **Internet** tem o valor **AuthenticodeRequired** e **UntrustedSites** tem o valor **desabilitado**.  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>Para restringir a lista de inclusão programaticamente  
  
1.  Crie um aplicativo de console do Visual Basic ou Visual c#.  
  
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
  
## <a name="disabling-the-inclusion-list"></a>Desativando a lista de inclusão  
 Você pode desativar a lista de inclusão para que os usuários finais só pode instalar soluções que sejam assinadas com um certificado confiável e conhecido.  
  
#### <a name="to-disable-the-inclusion-list"></a>Para desabilitar a lista de inclusão  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **iniciar**e, em seguida, clique em **executar**.  
  
    2.  No **abrir** , digite **regedt32.exe**e, em seguida, clique em **Okey**.  
  
2.  Se isso ainda não existir, crie a seguinte chave do registro:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Adicione as seguintes subchaves como **valor de cadeia de caracteres**, se ainda não existirem, com os valores associados.  
  
    |Subchave do valor de cadeia de caracteres|Valor|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Desabilitado**|  
    |**Internet**|**Desabilitado**|  
    |**Meu computador**|**Desabilitado**|  
    |**LocalIntranet**|**Desabilitado**|  
    |**TrustedSites**|**Desabilitado**|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>Para desabilitar a lista de inclusão programaticamente  
  
1.  Crie um aplicativo de console do Visual Basic ou Visual c#.  
  
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
 [Confiar em soluções do Office usando listas de inclusão](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)  
  
  