---
title: Depurando extensões para ferramentas do SharePoint no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7f976db455fc0cd847c648eb586b95fb81f6d5fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Depurando extensões para ferramentas do SharePoint no Visual Studio
  Você pode depurar extensões de ferramentas do SharePoint na instância experimental ou regular do Visual Studio. Se você precisar solucionar problemas de comportamento de uma extensão, você também pode modificar os valores do registro para exibir informações de erro adicionais e para configurar como o Visual Studio executa comandos do SharePoint.  
  
## <a name="debugging-extensions-in-the-experimental-instance-of-visual-studio"></a>Extensões de depuração na instância Experimental do Visual Studio  
 Para proteger seu ambiente de desenvolvimento do Visual Studio contra danos acidentais por extensões não testadas, o SDK do Visual Studio fornece uma instância alternativa do Visual Studio, chamada de *instância experimental*, que você pode usar Para instalar e testar as extensões. Desenvolver novas extensões usando a instância regular do Visual Studio, mas depurar e executá-los na instância experimental. Para obter mais informações, consulte [a instância Experimental](/visualstudio/extensibility/the-experimental-instance).  
  
 Se você usar um projeto do VSIX para implantar sua extensão, e o projeto do VSIX é o projeto de inicialização em sua solução, o Visual Studio automaticamente instala e executa a extensão na instância experimental ao depurar sua solução. O projeto de inicialização é o projeto que é iniciado quando você depura uma solução que contém vários projetos. Para obter mais informações sobre como usar um projeto do VSIX para implantar a sua extensão, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  

 Para obter exemplos que demonstram como depurar vários tipos de extensões na instância experimental do Visual Studio, consulte as instruções a seguir:  
  
-   [Instruções passo a passo: estendendo um tipo de item do projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Instruções passo a passo: criando um item de projeto de ação personalizado com um modelo de item, Parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Instruções passo a passo: criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Instruções passo a passo: estendendo o Gerenciador de Servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Instruções passo a passo: chamando o modelo do objeto de cliente do SharePoint em uma extensão do Gerenciador de Servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## <a name="debugging-extensions-in-the-regular-instance-of-visual-studio"></a>Extensões de depuração na instância Regular do Visual Studio  
 Se você deseja depurar seu projeto de extensão na instância regular do Visual Studio, primeiro instale a extensão na instância regular. Em seguida, anexe o depurador a um segundo processo do Visual Studio. Depois que você tiver terminado, você pode remover a extensão de forma que ele não mais carrega no computador de desenvolvimento.  
  
#### <a name="to-install-the-extension"></a>Para instalar a extensão  
  
1.  Feche todas as instâncias do Visual Studio.  
  
2.  Na pasta de saída de compilação para o projeto de extensão, abra o arquivo .vsix clicando duas vezes nele ou abrindo o menu de atalho e, em seguida, escolhendo **abrir**:  
  
3.  No **instalador de extensão do Visual Studio** caixa de diálogo caixa, escolha a edição do Visual Studio para o qual você deseja instalar a extensão e, em seguida, escolha o **instalar** botão.  
  
     Visual Studio instala os arquivos de extensão para %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*nome do autor*\\*nome de extensão* \\ *versão*. As últimas três pastas nesse caminho são construídas a partir de `Author`, `Name`, e `Version` elementos no arquivo extension.vsixmanifest para a extensão.  
  
4.  Depois que o Visual Studio instala a extensão, escolha o **fechar** botão.  
  
#### <a name="to-debug-the-extension"></a>Para depurar a extensão  
  
1.  Inicie o Visual Studio com privilégios de administrador e abra o projeto de extensão. As etapas a seguir fazem referência a essa instância do Visual Studio como o *primeiro instância*.  
  
2.  Inicie outra instância do Visual Studio com privilégios de administrador. As etapas a seguir fazem referência a essa instância do Visual Studio como o *segunda instância*.  
  
3.  Alterne para a primeira instância do Visual Studio.  
  
4.  Na barra de menus, escolha **depurar**, **anexar ao processo**.  
  
5.  No **processos disponíveis** , escolha devenv.exe. Essa entrada refere-se à segunda instância do Visual Studio; Essa é a instância que você deseja depurar na sua extensão de projeto.  
  
6.  Escolha o **Attach** botão.  
  
     No modo de depuração, o Visual Studio executará o projeto de extensão.  
  
7.  Alterne para a segunda instância do Visual Studio.  
  
8.  Crie um novo projeto do SharePoint que carrega sua extensão. Por exemplo, se você está depurando uma extensão para itens de projeto de definição de lista, crie um **definição de lista de** projeto.  
  
9. Execute todas as etapas são necessárias para testar seu código de extensão.  
  
10. Quando tiver terminado de depurar a extensão, feche a segunda instância do Visual Studio.  
  
#### <a name="to-remove-the-extension"></a>Para remover a extensão  
  
1.  No Visual Studio, na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
     A caixa de diálogo **Extensões e Atualizações** é aberta.  
  
2.  Na lista de extensões, escolha o nome da extensão e, em seguida, escolha o **desinstalação** botão.  
  
3.  Na caixa de diálogo que aparece, escolha o **Sim** botão para confirmar que você deseja desinstalar a extensão.  
  
4.  Escolha o **reiniciar agora** botão para concluir a desinstalação.  
  
## <a name="debugging-sharepoint-commands"></a>Depuração de comandos do SharePoint  
 Se você quiser depurar um comando do SharePoint que faz parte de uma extensão de ferramentas do SharePoint, você deve anexar o depurador ao processo vssphost4.exe. Este é o processo de host de 64 bits que executa comandos do SharePoint. Para obter mais informações sobre comandos do SharePoint e vssphost4.exe, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Para anexar o depurador ao processo vssphost4.exe  
  
1.  Inicie a depuração sua extensão na instância experimental do Visual Studio ou a instância regular do Visual Studio, seguindo as instruções acima.  
  
2.  Na instância do Visual Studio, no qual você estiver executando o depurador, na barra de menus, escolha **depurar**, **anexar ao processo**.  
  
3.  No **processos disponíveis** , escolha vssphost.exe.  
  
    > [!NOTE]  
    >  Se vssphost.exe não aparecer na lista, você deve iniciar o processo de vssphost4.exe na instância do Visual Studio, no qual você está executando a extensão. Normalmente, isso é feito executando uma ação que faz com que o Visual Studio para se conectar ao site do SharePoint no computador de desenvolvimento. Por exemplo, o Visual Studio inicia vssphost4.exe quando você expande um nó de conexão de site (um nó que exiba uma URL do site) sob o **conexões do SharePoint** nó no **Server Explorer** janela, ou quando você Adicione determinados itens de projeto do SharePoint, como **instância de lista** ou **receptor de evento** itens para um projeto do SharePoint.  
  
4.  Escolha o **Attach** botão.  
  
5.  Na instância do Visual Studio que está sendo depurado, execute as etapas que são necessárias para executar o comando.  
  
## <a name="modifying-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modificar valores de registro para ajudar a depurar SharePoint extensões de ferramentas  
 Quando você depura uma extensão de ferramentas do SharePoint no Visual Studio, você pode modificar os valores do registro para ajudar a solucionar a extensão. Os valores existem sob a chave HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools. Esses valores não existem por padrão.  
  
 Para ajudar a solucionar qualquer extensão de ferramentas do SharePoint, você pode criar e definir o valor de EnableDiagnostics. A tabela a seguir descreve esse valor.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|EnableDiagnostics|REG_DWORD que especifica se as mensagens de diagnóstico são exibidas no **saída** janela.<br /><br /> Para exibir mensagens de diagnóstico, defina esse valor como 1. Para interromper a exibição de mensagens, defina esse valor como 0 ou exclua esse valor.<br /><br /> Para gravar mensagens para o **saída** extensão das ferramentas de janela a partir do SharePoint, use o serviço de projeto do SharePoint. Para obter mais informações, consulte [usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|  
  
 Se sua extensão de incluir um comando do SharePoint, você pode criar e definir valores adicionais para ajudar a solucionar o comando. A tabela a seguir descreve esses valores.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|AttachDebuggerToHostProcess|REG_DWORD que especifica se deve exibir uma caixa de diálogo que permite que você anexe o depurador ao vssphost4.exe assim que ele é iniciado. Isso é útil se o comando que você deseja depurar é executado pelo vssphost.exe imediatamente após ele ser iniciado, e não há tempo suficiente para anexar o depurador manualmente antes do comando é executado. Para exibir a caixa de diálogo, chamadas de vssphost4.exe a <xref:System.Diagnostics.Debugger.Break%2A> método quando ele for iniciado.<br /><br /> Para habilitar esse comportamento, defina esse valor como 1. Para desativar esse comportamento, defina esse valor como 0 ou exclua esse valor.<br /><br /> Se você definir esse valor como 1, você talvez queira aumentar o valor de HostProcessStartupTimeout para dar tempo suficiente para anexar o depurador antes do Visual Studio espera vssphost4.exe para sinalizar que ele foi iniciado com êxito.|  
|ChannelOperationTimeout|REG_DWORD que especifica o tempo, em segundos, que o Visual Studio aguarda um comando do SharePoint a ser executado. Se o comando não é executado no momento, um <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> é gerada.<br /><br /> O padrão é 120 segundos.|  
|HostProcessStartupTimeout|REG_DWORD que especifica o tempo, em segundos, que o Visual Studio aguarda vssphost4.exe sinalizar que ele foi iniciado com êxito. Se vssphost4.exe não indica um início bem-sucedido no momento, um <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> é gerada.<br /><br /> O padrão é 60 segundos.|  
|maxReceivedMessageSize|REG_DWORD que especifica o tamanho máximo permitido, em bytes, das mensagens do WCF que são transmitidas entre o Visual Studio e vssphost4.exe.<br /><br /> O padrão é 1.048.576 bytes (1 MB).|  
|MaxStringContentLength|REG_DWORD que especifica o tamanho máximo permitido, em bytes, de cadeias de caracteres que são transmitidas entre o Visual Studio e vssphost4.exe.<br /><br /> O padrão é 1.048.576 bytes (1 MB).|  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Implantando extensões para as Ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  