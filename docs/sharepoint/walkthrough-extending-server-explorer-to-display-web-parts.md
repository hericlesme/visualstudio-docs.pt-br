---
title: 'Passo a passo: Estendendo o Gerenciador de servidores para exibir Web Parts | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34975f93b719c759707110907a3c19dabbd661c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-extending-server-explorer-to-display-web-parts"></a>Instruções passo a passo: estendendo o Gerenciador de Servidores para exibir Web Parts
  No Visual Studio, você pode usar o **conexões do SharePoint** nó de **Server Explorer** para exibir os componentes nos sites do SharePoint. No entanto, **Server Explorer** alguns componentes não são exibidos por padrão. Neste passo a passo, você estenderá a **Server Explorer** para que ele exibe a Galeria de Web Parts em cada conectado que o site do SharePoint.  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando uma extensão do Visual Studio que estende **Server Explorer** das seguintes maneiras:  
  
    -   A extensão adiciona um **Galeria de Web Parts** nó em cada nó do site do SharePoint no **Server Explorer**. Esse novo nó contém nós filho que representam cada Web Part na Galeria de Web Parts no site.  
  
    -   A extensão define um novo tipo de nó que representa uma instância de Web Part. Esse novo tipo de nó é a base para os nós filho sob a nova **Galeria de Web Parts** nó. O novo tipo de nó de Web Part exibe informações de **propriedades** janela sobre a Web Part que ele representa. O tipo de nó também inclui um item de menu de atalho personalizado que você pode usar como ponto de partida para executar outras tarefas relacionadas à Web Part.  
  
-   Criando dois comandos do SharePoint personalizados que as chamadas de assembly de extensão. Comandos do SharePoint são métodos que podem ser chamados por assemblies de extensão para usar APIs no modelo de objeto de servidor do SharePoint. Neste passo a passo, você deve criar comandos que recuperam informações de Web Part do site do SharePoint local no computador de desenvolvimento. Para obter mais informações, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Criando um pacote de extensão de Visual Studio (VSIX) para implantar a extensão.  
  
-   Depurando e testando a extensão.  
  
> [!NOTE]  
>  Para obter uma versão alternativa deste passo a passo que usa o modelo de objeto do cliente para o SharePoint, em vez de seu modelo de objeto de servidor, consulte [passo a passo: chamando o modelo de objeto de cliente do SharePoint em uma extensão do Gerenciador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisará dos seguintes componentes no computador de desenvolvimento para concluir este passo a passo:  
  
-   Edições com suporte do Windows, SharePoint e do Visual Studio. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   O SDK do Visual Studio. Este passo a passo usa o **projeto VSIX** modelo no SDK para criar um pacote do VSIX para implantar o item de projeto. Para obter mais informações, consulte [estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conhecimento sobre os conceitos a seguir é útil, mas não necessário para concluir o passo a passo:  
  
-   Usando o modelo de objeto do servidor do SharePoint. Para obter mais informações, consulte [usando o modelo de objeto do lado do servidor do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Web Parts em soluções do SharePoint. Para obter mais informações, consulte [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
 Para concluir este passo a passo, você deve criar três projetos:  
  
-   Um projeto do VSIX para criar o pacote do VSIX para implantar a extensão.  
  
-   Um projeto de biblioteca de classe que implementa a extensão. Este projeto deve usar o .NET Framework 4.5.  
  
-   Um projeto de biblioteca de classe que define os comandos do SharePoint personalizados. Este projeto deve usar o.NET Framework 3.5.  
  
 Criando projetos para iniciar o passo a passo.  
  
#### <a name="to-create-the-vsix-project"></a>Para criar o projeto do VSIX  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
3.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **extensibilidade** nó.  
  
    > [!NOTE]  
    >  O **extensibilidade** nó estará disponível somente se você instalar o SDK do Visual Studio. Para obter mais informações, consulte a seção pré-requisitos neste tópico.  
  
4.  Na parte superior da caixa de diálogo, escolha **.NET Framework 4.5** na lista de versões do .NET Framework.  
  
5.  Escolha o **projeto VSIX** modelo, nomeie o projeto **WebPartNode**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **WebPartNode** projeto **Gerenciador de soluções**.  
  
#### <a name="to-create-the-extension-project"></a>Para criar o projeto de extensão  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** nó ou **Visual Basic** nó e, em seguida, escolha **Windows** nó.  
  
3.  Na parte superior da caixa de diálogo, escolha **.NET Framework 4.5** na lista de versões do .NET Framework.  
  
4.  Na lista de modelos de projeto, escolha **biblioteca de classes**, nomeie o projeto **WebPartNodeExtension**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **WebPartNodeExtension** projeto à solução e abre o arquivo de código Class1 padrão.  
  
5.  Exclua o arquivo de código Class1 do projeto.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Para criar o projeto de comandos do SharePoint  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** nó ou **Visual Basic** nó e, em seguida, escolha o **Windows** nó.  
  
3.  Na parte superior da caixa de diálogo, escolha **.NET Framework 3.5** na lista de versões do .NET Framework.  
  
4.  
  
5.  Na lista de modelos de projeto, escolha **biblioteca de classes**, nomeie o projeto **WebPartCommands**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **WebPartCommands** projeto à solução e abre o arquivo de código Class1 padrão.  
  
6.  Exclua o arquivo de código Class1 do projeto.  
  
## <a name="configuring-the-projects"></a>Configurando projetos  
 Antes de escrever código para criar a extensão, você deve adicionar arquivos de código e referências de assembly e definir as configurações de projeto.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>Configurar o projeto WebPartNodeExtension  
  
1.  No projeto WebPartNodeExtension, adicione quatro arquivos de código que têm os seguintes nomes:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Abra o menu de atalho para o **WebPartNodeExtension** do projeto e, em seguida, escolha **adicionar referência**.  
  
3.  No **Gerenciador de referências - WebPartNodeExtension** caixa de diálogo caixa, escolha o **Framework** guia e, em seguida, selecione a caixa de seleção para cada um dos seguintes assemblies:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Escolha o **extensões** guia, marque a caixa de seleção para o assembly Microsoft.VisualStudio.SharePoint e, em seguida, escolha o **Okey** botão.  
  
5.  Em **Solution Explorer**, abra o menu de atalho para o **WebPartNodeExtension** nó do projeto e escolha **propriedades**.  
  
     O **Designer de Projeto** é aberto.  
  
6.  Escolha a guia **Aplicativo**.  
  
7.  No **namespace padrão** caixa (c#) ou **namespace raiz** caixa ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), digite **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Configurar o projeto WebPartCommands  
  
1.  No projeto WebPartCommands, adicione um arquivo de código que é chamado WebPartCommands.  
  
2.  Em **Solution Explorer**, abra o menu de atalho para o **WebPartCommands** nó do projeto, escolha **adicionar**e, em seguida, escolha **Item existente**.  
  
3.  No **Add Existing Item** caixa de diálogo, navegue até a pasta que contém os arquivos de código para o projeto WebPartNodeExtension e, em seguida, escolha os arquivos de código WebPartNodeInfo e WebPartCommandIds.  
  
4.  Clique na seta ao lado de **adicionar** botão e, em seguida, escolha **adicionar como vínculo** no menu que aparece.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona os arquivos de código ao projeto WebPartCommands como links. Como resultado, os arquivos de código estão localizados no projeto WebPartNodeExtension, mas o código nos arquivos também são compilados no projeto WebPartCommands.  
  
5.  Abra o menu de atalho para o **WebPartCommands** projeto novamente e escolha **adicionar referência**.  
  
6.  No **Gerenciador de referências - WebPartCommands** caixa de diálogo caixa, escolha o **extensões** guia, marque a caixa de seleção para cada um dos seguintes assemblies e, em seguida, escolha o **Okey** botão:  
  
    -   Microsoft. SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  Em **Solution Explorer**, abra o menu de atalho para o **WebPartCommands** projeto novamente e, em seguida, escolha **propriedades**.  
  
     O **Designer de Projeto** é aberto.  
  
8.  Escolha a guia **Aplicativo**.  
  
9. No **namespace padrão** caixa (c#) ou **namespace raiz** caixa ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), digite **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Criando ícones para novos nós  
 Criar dois ícones para o **Server Explorer** extensão: um ícone para o novo **Galeria de Web Parts** nó e outro ícone para cada nó de Web Part filho sob o **Galeria de Web Parts** nó. Posteriormente neste passo a passo, você escreverá código que associa esses ícones com os nós.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Para criar ícones para os nós  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **WebPartNodeExtension** do projeto e, em seguida, escolha **propriedades**.  
  
2.  O **Designer de Projeto** é aberto.  
  
3.  Escolha o **recursos** guia e, em seguida, escolha o **este projeto não contém um arquivo de recursos padrão. Clique aqui para criar um** link.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] cria um arquivo de recurso e abre-o no designer.  
  
4.  Na parte superior do designer, clique na seta ao lado de **adicionar recurso** menu de comando e, em seguida, escolha **adicionar novo ícone** no menu que aparece.  
  
5.  No **adicionar novo recurso** caixa de diálogo, o nome do novo ícone **WebPartsNode**e, em seguida, escolha o **adicionar** botão.  
  
     O novo ícone é aberto no **Editor de imagem**.  
  
6.  Edite a versão de 16x16 do ícone de forma que ele tem um design que você pode reconhecer facilmente.  
  
7.  Abra o menu de atalho para a versão de 32 x 32 do ícone e, em seguida, escolha **excluir tipo de imagem**.  
  
8.  Repita as etapas 5 a 8 para adicionar um ícone de segundo para os recursos de projeto e nomeie esse ícone **WebPart**.  
  
9. No **Gerenciador de soluções**, sob o **recursos** pasta para o **WebPartNodeExtension** projeto, abra o menu de atalho **WebPartsNode.ico**.  
  
10. No **propriedades** janela, clique na seta ao lado de **ação de compilação**e, em seguida, escolha **recurso incorporado** no menu que aparece.  
  
11. Repita as duas últimas etapas para **WebPart.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Adicionar o nó da Galeria de Web Parts ao Gerenciador de servidores  
 Crie uma classe que adiciona o novo **Galeria de Web Parts** nó para cada nó do site do SharePoint. Para adicionar o novo nó, a classe implementa o <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Implementar essa interface, sempre que você deseja estender o comportamento de um nó existente no **Gerenciador de servidores**, como adicionar um nó filho em um nó.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Para adicionar o nó de galeria de Web Parts ao Gerenciador de servidores  
  
1.  No projeto WebPartNodeExtension, abra o arquivo de código SiteNodeExtension e, em seguida, cole o seguinte código para ele.  
  
    > [!NOTE]  
    >  Depois que você adicione esse código, o projeto terá alguns erros de compilação, mas vai desaparecer quando você adiciona o código em etapas posteriores.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Definir um tipo de nó que representa uma Web Part  
 Crie uma classe que define um novo tipo de nó que representa uma Web Part. O Visual Studio usa esse novo tipo de nó para exibir nós filho sob o **Galeria de Web Parts** nó. Cada nó filho representa uma única parte da Web no site do SharePoint.  
  
 Para definir o novo tipo de nó, a classe implementa o <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Implementar essa interface, sempre que você deseja definir um novo tipo de nó no **Server Explorer**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Para definir o tipo de nó de Web Part  
  
1.  No projeto WebPartNodeExtension, abra o arquivo de código WebPartNodeTypeProvder e, em seguida, cole o seguinte código para ele.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="defining-the-web-part-data-class"></a>Definição da classe de dados da Web Part  
 Defina uma classe que contém dados sobre uma única parte da Web no site do SharePoint. Posteriormente neste passo a passo, você criará um comando do SharePoint personalizado que recupera dados sobre cada Web Part no site e, em seguida, atribui os dados para as instâncias dessa classe.  
  
#### <a name="to-define-the-web-part-data-class"></a>Para definir a classe de dados de Web Part  
  
1.  No projeto WebPartNodeExtension, abra o arquivo de código WebPartNodeInfo e, em seguida, cole o seguinte código para ele.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="defining-the-ids-for-the-sharepoint-command"></a>Definindo as IDs de comando do SharePoint  
 Defina várias cadeias de caracteres que identificam os comandos do SharePoint personalizados. Você irá implementar esses comandos posteriormente neste passo a passo.  
  
#### <a name="to-define-the-command-ids"></a>Para definir as IDs de comando  
  
1.  No projeto WebPartNodeExtension, abra o arquivo de código WebPartCommandIds e, em seguida, cole o seguinte código para ele.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Criando os comandos do SharePoint personalizado  
 Crie comandos personalizados que chamam o modelo de objeto de servidor do SharePoint para recuperar dados sobre as Web Parts no site do SharePoint. Cada comando é um método que tem o <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> aplicada a ele.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Para definir os comandos do SharePoint  
  
1.  No projeto WebPartCommands, abra o arquivo de código WebPartCommands e, em seguida, cole o seguinte código para ele.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Nesse ponto no passo a passo, todo o código para o **Galeria de Web Parts** nó e os comandos do SharePoint agora estão nos projetos. Compile a solução para certificar-se de que ambos os projetos compilar sem erros.  
  
#### <a name="to-build-the-solution"></a>Para compilar a solução  
  
1.  Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
    > [!WARNING]  
    >  Neste ponto, o projeto WebPartNode pode ter um erro de compilação porque o arquivo de manifesto do VSIX não tem um valor para o autor. Esse erro desaparecerá quando você adiciona um valor em etapas posteriores.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Criando um pacote do VSIX para implantar a extensão  
 Para implantar a extensão, use o projeto do VSIX em sua solução para criar um pacote do VSIX. Primeiro, configure o pacote VSIX, modificando o arquivo source.extension.vsixmanifest no projeto do VSIX. Em seguida, crie o pacote do VSIX por compilar a solução.  
  
#### <a name="to-configure-the-vsix-package"></a>Para configurar o pacote VSIX  
  
1.  Em **Solution Explorer**, no projeto WebPartNode, abra o **source.extension.vsixmanifest** arquivo no editor de manifesto.  
  
     O arquivo source.extension.vsixmanifest é a base para o arquivo extension.vsixmanifest que necessitam de todos os pacotes VSIX. Para obter mais informações sobre esse arquivo, consulte [1.0 referência do esquema de extensão de VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  No **nome do produto** , digite **Web Part Galeria nó Gerenciador de servidores**.  
  
3.  No **autor** , digite **Contoso**.  
  
4.  No **descrição** , digite **adiciona um nó de galeria de Web Parts personalizado para o nó conexões do SharePoint no Gerenciador de servidores. Essa extensão usa um comando do SharePoint personalizado para chamar o modelo de objeto do servidor.**  
  
5.  Escolha o **ativos** guia do editor e, em seguida, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
6.  No **tipo** , escolha **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Esse valor corresponde do `MefComponent` elemento no arquivo extension.vsixmanifest. Este elemento Especifica o nome de um assembly de extensão do pacote VSIX. Para obter mais informações, consulte [MEFComponent Element (esquema de VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  No **fonte** , escolha **um projeto na solução atual**.  
  
8.  No **projeto** , escolha **WebPartNodeExtension** e, em seguida, escolha o **Okey** botão.  
  
9. No editor de manifesto, escolha o **novo** novamente.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
10. No **tipo** , digite **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Este elemento Especifica uma extensão personalizada que você deseja incluir na extensão do Visual Studio. Para obter mais informações, consulte [elemento ativo (esquema VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. No **fonte** , escolha o **um projeto na solução atual** item de lista.  
  
12. No **projeto** , escolha **WebPartCommands**e, em seguida, escolha o **Okey** botão.  
  
13. Na barra de menus, escolha **criar**, **compilar solução**e, em seguida, certifique-se de que a solução compilado sem erros.  
  
14. Certifique-se de que a pasta de saída de compilação do projeto WebPartNode agora contém o arquivo WebPartNode.vsix.  
  
     Por padrão, a pasta de saída de compilação é o. pasta \bin\debug sob a pasta que contém o arquivo de projeto.  
  
## <a name="testing-the-extension"></a>A extensão de teste  
 Agora você está pronto para testar o novo **Galeria de Web Parts** nó **Server Explorer**. Primeiro, inicie a depuração a extensão em uma instância experimental do Visual Studio. Em seguida, use o novo **Web Parts** nó na instância experimental do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>Para iniciar a depuração de extensão  
  
1.  Reiniciar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] com credenciais administrativas e, em seguida, abra a solução WebPartNode.  
  
2.  No projeto WebPartNodeExtension, abra o arquivo de código SiteNodeExtension e, em seguida, adicione um ponto de interrupção para a primeira linha do código no `NodeChildrenRequested` e `CreateWebPartNodes` métodos.  
  
3.  Pressione a tecla F5 para iniciar a depuração.  
  
     O Visual Studio instala a extensão %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web extensão de nó de galeria de parte para servidor Explorer\1.0 e inicia uma instância experimental do Visual Studio. Você testará o item de projeto nesta instância do Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Para testar a extensão  
  
1.  Na instância experimental do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na barra de menus, escolha **exibição**, **Server Explorer**.  
  
2.  Execute as seguintes etapas se o site do SharePoint que você deseja usar para teste não aparecer sob o **conexões do SharePoint** nó **Server Explorer**:  
  
    1.  Em **Server Explorer**, abra o menu de atalho para **conexões do SharePoint**e, em seguida, escolha **Adicionar Conexão**.  
  
    2.  No **Adicionar Conexão do SharePoint** caixa de diálogo caixa, digite a URL do site do SharePoint ao qual você deseja se conectar e, em seguida, escolha o **Okey** botão.  
  
         Para especificar o site do SharePoint no computador de desenvolvimento, digite **http://localhost**.  
  
3.  Expanda o nó de conexão de site (que exibe a URL do seu site) e, em seguida, expanda um nó filho do site (por exemplo, **Site de equipe**).  
  
4.  Verifique o código na instância do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] será interrompido no ponto de interrupção que você definiu anteriormente no `NodeChildrenRequested` método e pressione F5 para continuar a depuração do projeto.  
  
5.  A instância experimental do Visual Studio, verifique se que um novo nó denominado **Galeria de Web Parts** aparece sob o nó do site de nível superior e, em seguida, expanda o **Galeria de Web Parts** nó.  
  
6.  Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definiu anteriormente no `CreateWebPartNodes` método e, em seguida, escolha a tecla F5 para continuar a depuração do projeto.  
  
7.  Na instância experimental do Visual Studio, verifique se todas as Web Parts no site conectado aparecem sob o **Galeria de Web Parts** nó **Server Explorer**.  
  
8.  Em **Server Explorer**, abra o menu de atalho para uma das Web Parts e, em seguida, escolha **propriedades**.  
  
9. Na instância do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que você está depurando, verifique se os detalhes sobre a Web Part aparecem no **propriedades** janela.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Desinstalar a extensão do Visual Studio  
 Depois de concluir o teste de extensão, desinstale a extensão do Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar a extensão  
  
1.  Na instância experimental do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
     A caixa de diálogo **Extensões e Atualizações** é aberta.  
  
2.  Na lista de extensões, escolha **Web Part Galeria nó extensão para o Gerenciador de servidores**e, em seguida, escolha o **desinstalação** botão.  
  
3.  Na caixa de diálogo que aparece, escolha o **Sim** botão para confirmar que você deseja desinstalar a extensão e, em seguida, escolha o **reiniciar agora** botão para concluir a desinstalação.  
  
4.  Feche ambas as instâncias do Visual Studio (a instância experimental e a instância do Visual Studio, em que a solução WebPartNode estiver aberta).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Passo a passo: Chamando o modelo de objeto de cliente do SharePoint em uma extensão do Gerenciador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons)   
 [Criando um ícone ou outra imagem &#40;Editor de imagens para ícones&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  