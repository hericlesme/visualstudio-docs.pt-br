---
title: 'Passo a passo: Chamando o modelo de objeto de cliente do SharePoint em uma extensão do Gerenciador de servidores | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4951d9960a3027e8d72bb0fbc72d551f123993ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Instruções passo a passo: chamando o modelo do objeto de cliente do SharePoint em uma extensão do Gerenciador de Servidores
  Este passo a passo demonstra como chamar o modelo de objeto do cliente do SharePoint de uma extensão para o **conexões do SharePoint** nó **Server Explorer**. Para obter mais informações sobre como usar o modelo de objeto do cliente do SharePoint, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensão que estende o **conexões do SharePoint** nó de **Server Explorer** das seguintes maneiras:  
  
    -   A extensão adiciona um **Galeria de Web Parts** nó em cada nó do site do SharePoint no **Server Explorer**. Esse novo nó contém nós filho que representam cada Web Part na Galeria de Web Parts no site.  
  
    -   A extensão define um novo tipo de nó que representa uma instância de Web Part. Esse novo tipo de nó é a base para os nós filho sob a nova **Galeria de Web Parts** nó. O novo tipo de nó de Web Part exibe informações de **propriedades** janela sobre a Web Part que representa o nó.  
  
-   Criando um pacote de extensão de Visual Studio (VSIX) para implantar a extensão.  
  
-   Depurando e testando a extensão.  
  
> [!NOTE]  
>  A extensão que você cria neste passo a passo é semelhante a extensão que você criar no [passo a passo: estendendo o Gerenciador de servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Essa explicação passo a passo usa o modelo de objeto de servidor do SharePoint, mas este passo a passo realiza as mesmas tarefas usando o modelo de objeto do cliente.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisará dos seguintes componentes no computador de desenvolvimento para concluir este passo a passo:  
  
-   Edições com suporte do Windows, o SharePoint e o Visual Studio. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   O SDK do Visual Studio. Este passo a passo usa o **projeto VSIX** modelo no SDK para criar um pacote do VSIX para implantar a extensão. Para obter mais informações, consulte [estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
Conhecimento sobre os conceitos a seguir é útil, mas não necessário para concluir o passo a passo:  
  
-   Usando o modelo de objeto do cliente do SharePoint. Para obter mais informações, consulte [modelo de objeto gerenciado do cliente](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Web parts do SharePoint. Para obter mais informações, consulte [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
 Para concluir este passo a passo, você deve criar dois projetos:  
  
-   Um projeto do VSIX para criar o pacote do VSIX para implantar o **Server Explorer** extensão.  
  
-   Um projeto de biblioteca de classe que implementa o **Server Explorer** extensão.  
  
 Criando projetos para iniciar o passo a passo.  
  
#### <a name="to-create-the-vsix-project"></a>Para criar o projeto do VSIX  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
3.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha **extensibilidade**.  
  
    > [!NOTE]  
    >  O **extensibilidade** nó estará disponível somente se você instalar o SDK do Visual Studio. Para obter mais informações, consulte a seção pré-requisitos neste tópico.  
  
4.  Na parte superior da caixa de diálogo, escolha **.NET Framework 4.5** na lista de versões do .NET Framework.  
  
     Extensões de ferramentas do SharePoint exigem recursos nesta versão do .NET Framework.  
  
5.  Escolha o **projeto VSIX** modelo.  
  
6.  No **nome** , digite **WebPartNode**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **WebPartNode** projeto **Gerenciador de soluções**.  
  
#### <a name="to-create-the-extension-project"></a>Para criar o projeto de extensão  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha **Windows**.  
  
3.  Na parte superior da caixa de diálogo, escolha **.NET Framework 4.5** na lista de versões do .NET Framework.  
  
4.  Na lista de modelos de projeto, escolha **biblioteca de classes**.  
  
5.  No **nome** , digite **WebPartNodeExtension**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **WebPartNodeExtension** projeto à solução e abre o arquivo de código Class1 padrão.  
  
6.  Exclua o arquivo de código Class1 do projeto.  
  
## <a name="configuring-the-extension-project"></a>Configurando o projeto de extensão  
 Antes de escrever código para criar a extensão, você deve adicionar referências de assembly ao seu projeto e arquivos de código, e você deve atualizar o namespace padrão.  
  
#### <a name="to-configure-the-project"></a>Configurar o projeto  
  
1.  No **WebPartNodeExtension** de projeto, adicione dois arquivos de código que são nomeados SiteNodeExtension e WebPartNodeTypeProvider.  
  
2.  Abra o menu de atalho para o projeto WebPartNodeExtension e, em seguida, escolha **adicionar referência**.  
  
3.  No **Gerenciador de referências - WebPartNodeExtension** caixa de diálogo caixa, escolha o **Framework** nó e, em seguida, selecione as caixas de seleção para o System.ComponentModel.Composition e System módulos (assemblies).  
  
4.  Escolha o **extensões** nó, selecione a caixa de seleção para cada um dos seguintes assemblies e, em seguida, escolha o **Okey** botão:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Abra o menu de atalho para o **WebPartNodeExtension** do projeto e, em seguida, escolha **propriedades**.  
  
     O **Designer de Projeto** é aberto.  
  
6.  Escolha a guia **Aplicativo**.  
  
7.  No **namespace padrão** caixa (c#) ou **namespace raiz** (Visual Basic), digite **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Criando ícones para novos nós  
 Criar dois ícones para o **Server Explorer** extensão: um ícone para o novo **Galeria de Web Parts** nó e outro ícone para cada nó de Web Part filho sob o **Galeria de Web Parts** nó. Posteriormente neste passo a passo, você vai escrever código que associa esses ícones com os nós.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Para criar ícones para os nós  
  
1.  No **Project Designer** para o projeto WebPartNodeExtension, escolha o **recursos** guia.  
  
2.  Escolha o link **este projeto não contém um arquivo de recursos padrão. Clique aqui para criar um.**  
  
     Visual Studio cria um arquivo de recurso e abre-o no designer.  
  
3.  Na parte superior do designer, clique na seta no **adicionar recurso** menu de comando e, em seguida, escolha **adicionar novo ícone**.  
  
4.  Digite **WebPartsNode** para o novo nome e, em seguida, escolha o **adicionar** botão.  
  
     O novo ícone é aberto no **Editor de imagem**.  
  
5.  Edite a versão de 16x16 do ícone de forma que ele tem um design que você pode reconhecer facilmente.  
  
6.  Abra o menu de atalho para a versão de 32 x 32 do ícone e, em seguida, escolha **excluir tipo de imagem**.  
  
7.  Repita as etapas 3 a 7 para adicionar um ícone de segundo para os recursos de projeto e nomeie esse ícone **WebPart**.  
  
8.  Em **Solution Explorer**, no **recursos** pasta para o **WebPartNodeExtension** de projeto, escolha **WebPartsNode.ico**.  
  
9. No **propriedades** janela, abra o **ação de compilação** lista e, em seguida, escolha **recurso inserido**.  
  
10. Repita as duas últimas etapas para **WebPart.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Adicionar o nó da Galeria de Web Parts ao Gerenciador de servidores  
 Crie uma classe que adiciona o novo **Galeria de Web Parts** nó para cada nó do site do SharePoint. Para adicionar o novo nó, a classe implementa o <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Implementar essa interface, sempre que você deseja estender o comportamento de um nó existente no **Gerenciador de servidores**, como adicionar um novo nó filho em um nó.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Para adicionar o nó de galeria de Web Parts ao Gerenciador de servidores  
  
1.  Cole o seguinte código para o **SiteNodeExtension** arquivo de código para o **WebPartNodeExtension** projeto.  
  
    > [!NOTE]  
    >  Depois de adicionar esse código, o projeto terá alguns erros de compilação. Esses erros desaparecerá quando você adiciona o código em etapas posteriores.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Definir um tipo de nó que representa uma Web Part  
 Crie uma classe que define um novo tipo de nó que representa uma Web Part. O Visual Studio usa esse novo tipo de nó para exibir nós filho sob o **Galeria de Web Parts** nó. Cada um de nós filho representa uma única parte da Web no site do SharePoint.  
  
 Para definir o novo tipo de nó, a classe implementa o <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Implementar essa interface, sempre que você deseja definir um novo tipo de nó no **Server Explorer**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Para definir o tipo de nó de Web Part  
  
1.  Cole o seguinte código para o **WebPartNodeTypeProvider** arquivo de código para o **WebPartNodeExtension** projeto.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Nesse ponto no passo a passo, todo o código para o **Galeria de Web Parts** nó está agora no projeto. Criar o **WebPartNodeExtension** projeto para certificar-se de que ele foi compilado sem erros.  
  
#### <a name="to-build-the-project"></a>Para compilar o projeto  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **WebPartNodeExtension** do projeto e, em seguida, escolha **criar**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Criando um pacote do VSIX para implantar a extensão  
 Para implantar a extensão, use o projeto do VSIX em sua solução para criar um pacote do VSIX. Primeiro, configure o pacote VSIX, modificando o arquivo source.extension.vsixmanifest que está incluído no projeto. Crie o pacote do VSIX por compilar a solução.  
  
#### <a name="to-configure-the-vsix-package"></a>Para configurar o pacote VSIX  
  
1.  Em **Solution Explorer**, no **WebPartNode** projeto, abra **source.extension.vsixmanifest** arquivo no editor de manifesto.  
  
     O arquivo source.extension.vsixmanifest é a base para o arquivo extension.vsixmanifest que necessitam de todos os pacotes VSIX. Para obter mais informações sobre esse arquivo, consulte [1.0 referência do esquema de extensão de VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  No **nome do produto** , digite **Web Part Galeria nó Gerenciador de servidores**.  
  
3.  No **autor** , digite **Contoso**.  
  
4.  No **descrição** , digite **adiciona um nó de galeria de Web Parts personalizado para o nó conexões do SharePoint no Gerenciador de servidores**.  
  
5.  Sobre o **ativos** guia do editor, escolha o **novo** botão.  
  
6.  No **adicionar novo ativo** na caixa de **tipo** , escolha **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Esse valor corresponde do `MefComponent` elemento no arquivo extension.vsixmanifest. Este elemento Especifica o nome de um assembly de extensão do pacote VSIX. Para obter mais informações, consulte [MEFComponent Element (esquema de VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  No **fonte** , escolha **um projeto na solução atual**.  
  
8.  No **projeto** , escolha **WebPartNodeExtension**e, em seguida, escolha o **Okey** botão.  
  
9. Na barra de menus, escolha **criar**, **compilar solução**e, em seguida, certifique-se de que a solução compilado sem erros.  
  
10. Certifique-se de que a pasta de saída de compilação do projeto WebPartNode agora contém o arquivo WebPartNode.vsix.  
  
     Por padrão, a pasta de saída de compilação é o. pasta \bin\debug sob a pasta que contém o arquivo de projeto.  
  
## <a name="testing-the-extension"></a>A extensão de teste  
 Agora você está pronto para testar o novo **Galeria de Web Parts** nó **Server Explorer**. Primeiro, inicie depurar o projeto de extensão em uma instância experimental do Visual Studio. Em seguida, usar o novo **Web Parts** nó na instância experimental do Visual Studio.  
  
#### <a name="to-start-debugging-the-extension"></a>Para iniciar a depuração de extensão  
  
1.  Reinicie o Visual Studio com credenciais administrativas e, em seguida, abra o **WebPartNode** solução.  
  
2.  No projeto WebPartNodeExtension, abra o **SiteNodeExtension** arquivo de código e, em seguida, adicione um ponto de interrupção para as linhas de código no `NodeChildrenRequested` e `CreateWebPartNodes` métodos.  
  
3.  Pressione a tecla F5 para iniciar a depuração.  
  
     O Visual Studio instala a extensão %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web extensão de nó de galeria de parte para servidor Explorer\1.0 e inicia uma instância experimental do Visual Studio. Você testará o item de projeto nesta instância do Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Para testar a extensão  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **exibição**, **Server Explorer**.  
  
2.  Verifique se o site do SharePoint que você deseja usar para teste aparece sob o **conexões do SharePoint** nó **Server Explorer**. Se não estiver listado, siga estas etapas:  
  
    1.  Abra o menu de atalho para **conexões do SharePoint**e, em seguida, escolha **Adicionar Conexão**.  
  
    2.  No **Adicionar Conexão do SharePoint** caixa de diálogo caixa, digite a URL do site do SharePoint ao qual você deseja se conectar e, em seguida, escolha o **Okey** botão.  
  
         Para especificar o site do SharePoint no computador de desenvolvimento, digite **http://localhost**.  
  
3.  Expanda o nó de conexão de site (que exibe a URL do seu site) e, em seguida, expanda um nó filho do site (por exemplo, **Site de equipe**).  
  
4.  Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definiu anteriormente no `NodeChildrenRequested` método e, em seguida, escolha a tecla F5 para continuar a depuração do projeto.  
  
5.  Na instância experimental do Visual Studio, expanda o **Galeria de Web Parts** nó, que aparece sob o nó do site de nível superior.  
  
6.  Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definiu anteriormente no `CreateWebPartNodes` método e, em seguida, escolha a tecla F5 para continuar a depuração do projeto.  
  
7.  Na instância experimental do Visual Studio, verifique se todas as partes da Web no site conectado aparecem sob o **Galeria de Web Parts** nó **Server Explorer**.  
  
8.  Abra o menu de atalho para uma Web Part e, em seguida, escolha **propriedades**.  
  
9. No **propriedades** janela, verifique se os detalhes sobre a Web Part aparecem.  
  
10. Em **Server Explorer**, abra o menu de atalho para a Web Part do mesmo e, em seguida, escolha **Exibir mensagem**.  
  
     Na caixa de mensagem que aparece, escolha o **Okey** botão.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Desinstalar a extensão do Visual Studio  
 Depois de concluir o teste de extensão, você deve desinstalá-lo do Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar a extensão  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
     A caixa de diálogo **Extensões e Atualizações** é aberta.  
  
2.  Na lista de extensões, escolha **Web Part Galeria nó Gerenciador de servidores**e, em seguida, escolha o **desinstalação** botão.  
  
3.  Na caixa de diálogo que aparece, escolha o **Sim** botão.  
  
4.  Escolha o **reiniciar agora** botão para concluir a desinstalação.  
  
     O item de projeto também será desinstalado.  
  
5.  Feche ambas as instâncias do Visual Studio (a instância experimental e a instância do Visual Studio, em que a solução WebPartNode estiver aberta).  
  
## <a name="see-also"></a>Consulte também  
 [A chamada para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Passo a passo: Estendendo o Gerenciador de servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons)   
 [Criando um ícone ou outra imagem &#40;Editor de imagens para ícones&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  