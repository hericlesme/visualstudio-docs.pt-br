---
title: "Usar o repositório de configurações | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ecb7cf4a40793116159bd2ff8292f0303e3cc46f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-settings-store"></a>Usar o repositório de configurações
Há dois tipos de repositórios de configurações:  
  
-   Definições de configuração, que são configurações do Visual Studio e VSPackage somente leitura. O Visual Studio mescla as configurações de todos os arquivos .pkgdef conhecidos neste repositório.  
  
-   Configurações de usuário, que são configurações graváveis, como aqueles que são exibidos em páginas de **opções** caixa de diálogo, páginas de propriedade e certas outras caixas de diálogo. Extensões do Visual Studio podem usá-los para o armazenamento local de pequenas quantidades de dados.  
  
 Este passo a passo mostra como ler dados do repositório de configuração de configuração. Consulte [gravar no repositório de configurações do usuário](../extensibility/writing-to-the-user-settings-store.md) para obter uma explicação de como escrever para o repositório de configurações do usuário.  
  
## <a name="creating-the-example-project"></a>Criando o projeto de exemplo  
 Esta seção mostra como criar um projeto de extensão simples com um comando de menu para demonstração.  
  
1.  Cada extensão do Visual Studio inicia com um projeto de implantação do VSIX que conterá os ativos de extensão. Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto VSIX chamado `SettingsStoreExtension`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual C# / extensibilidade**.  
  
2.  Agora, adicione um modelo de item de comando personalizado chamado **SettingsStoreCommand**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual C# / extensibilidade** e selecione **comando personalizado**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para **SettingsStoreCommand.cs**. Para obter mais informações sobre como criar um comando personalizado, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Usando o armazenamento de definições de configuração  
 Esta seção mostra como detectar e exibir as definições de configuração.  
  
1.  No arquivo SettingsStorageCommand.cs, adicione o seguinte usando instruções:  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  Em `MenuItemCallback`, remova o corpo do método e adicionar essas linhas obtém repositório de configurações de configuração:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     O <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> é uma classe auxiliar gerenciado sobre o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> service.  
  
3.  Agora, descubra se as ferramentas do Windows Phone são instaladas. O código deve ter esta aparência:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Teste o código. Compile o projeto e comece a depuração.  
  
5.  Na instância experimental, sobre o **ferramentas** menu, clique em **SettingsStoreCommand invocar**.  
  
     Você deve ver uma caixa de texto **ferramentas de desenvolvedor do Microsoft Windows Phone:** seguido por **True** ou **False**.  
  
 O Visual Studio manterá o repositório de configurações no registro do sistema.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Para usar um editor de registro para verificar as definições de configuração  
  
1.  Abra o Regedit.exe.  
  
2.  Navegue até HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Certifique-se de que você está vendo a chave que contém \14.0Exp_Config\ e não \14.0_Config\\. Quando você executa a instância experimental do Visual Studio, as configurações estão na seção do Registro "14.0Exp_Config".  
  
3.  Expanda o nó \Installed Products\. Se a mensagem nas etapas anteriores for **instalado de ferramentas de desenvolvedor do Microsoft Windows Phone: True**, em seguida, \Installed Products\ deve conter um nó de ferramentas de desenvolvedor do Microsoft Windows Phone. Se a mensagem for **instalado de ferramentas de desenvolvedor do Microsoft Windows Phone: False**, em seguida, \Installed Products\ não deve conter um nó de ferramentas de desenvolvedor do Microsoft Windows Phone.