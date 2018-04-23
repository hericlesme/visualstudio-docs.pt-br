---
title: Obtendo informações do serviço de repositório de configurações | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11731e36517ae6245dddd1ebdd3b002fb3c37391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="getting-service-information-from-the-settings-store"></a>Obtendo informações do serviço de repositório de configurações
Você pode usar o repositório de configurações para localizar todos os serviços disponíveis ou para determinar se um serviço específico está instalado. Você deve saber o tipo de classe de serviço.  
  
### <a name="to-list-the-available-services"></a>Para listar os serviços disponíveis  
  
1.  Crie um projeto do VSIX denominado FindServicesExtension e, em seguida, adicionar um comando personalizado chamado FindServicesCommand. Para obter mais informações sobre como criar um comando personalizado, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  Em FindServicesCommand.cs, adicione o seguinte usando instruções:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Obter o armazenamento de definições de configuração e, em seguida, localizar a subcoleção chamada Services. Esta coleção inclui todos os serviços disponíveis. No método MenuItemCommand, remova o código existente e substitua-o com o seguinte:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Compile o projeto e comece a depuração. A instância experimental aparece.  
  
5.  Na instância experimental, sobre o **ferramentas** menu, clique em **FindServicesCommand invocar**.  
  
     Você deve ver uma caixa de mensagem listando todos os serviços.  
  
     Para verificar essas configurações, você pode usar o editor do registro.  
  
## <a name="finding-a-specific-service"></a>Localizando um serviço específico  
 Você também pode usar o <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> método para determinar se um serviço específico está instalado. Você deve saber o tipo de classe de serviço.  
  
1.  Na MenuItemCallback do projeto que você criou no procedimento anterior, pesquise o repositório de configurações de configuração para o `Services` coleção que tem a subcoleção chamada pelo GUID do serviço. Nesse caso, abordaremos para o serviço de Ajuda.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2.  Compile o projeto e comece a depuração.  
  
3.  Na instância experimental, sobre o **ferramentas** menu, clique em **FindServicesCommand invocar**.  
  
     Você verá uma mensagem com o texto **ajuda serviço disponível:** seguido por **True** ou **False**. Para verificar essa configuração, você pode usar um editor de registro, conforme mostrado nas etapas anteriores.