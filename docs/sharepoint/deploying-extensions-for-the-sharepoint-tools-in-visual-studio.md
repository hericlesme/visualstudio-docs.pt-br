---
title: "Implantando extensões para ferramentas do SharePoint no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 80cc884e45d9db10f6552fa44e611e87b7b4f801
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="deploying-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Implantando extensões para as ferramentas do SharePoint no Visual Studio
  Para implantar uma extensão de ferramentas do SharePoint, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) que contém o assembly de extensão e outros arquivos que você quer distribuir com a extensão. Um pacote do VSIX é um arquivo compactado que segue o padrão de Open Packaging Conventions (OPC). Pacotes do VSIX tem a extensão de .vsix.  
  
 Depois de criar um pacote do VSIX, outros usuários possam executar o arquivo .vsix para instalar a extensão. Quando um usuário instala a extensão, todos os arquivos são instalados na pasta %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Para implantar a extensão, você pode carregar o pacote do VSIX para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web, ou você pode distribuir o pacote para os clientes por outros meios, como o pacote em um compartilhamento de rede ou algum outro site de hospedagem.  
  
 Para obter mais informações sobre como criar pacotes VSIX e implantá-los para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), consulte [envio extensões do Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
 Você pode criar um pacote do VSIX usando o **projeto VSIX** modelo no Visual Studio, ou você pode criar um pacote do VSIX manualmente.  
  
## <a name="using-vsix-projects-to-create-vsix-packages"></a>Usando projetos do VSIX para criar pacotes VSIX  
 Você pode usar o **projeto VSIX** modelo fornecido pelo SDK do Visual Studio para criar pacotes VSIX para extensões de ferramentas do SharePoint. Usando um projeto do VSIX oferece várias vantagens sobre a criação de um pacote do VSIX manualmente:  
  
-   O Visual Studio gera automaticamente o pacote do VSIX quando você compilar o projeto. Tarefas como adicionar os arquivos de implantação para o pacote e criar o arquivo. XML de [Content_Types] para o pacote são feitas para você.  
  
-   Você pode configurar o projeto do VSIX para incluir a saída da compilação do seu projeto de extensão e outros arquivos, como modelos de projeto e modelos de item no pacote do VSIX.  
  
 Para obter mais informações sobre como usar um projeto VSIX, consulte [modelo de projeto do VSIX](/visualstudio/extensibility/vsix-project-template).  
  
### <a name="organizing-your-projects"></a>Organizar seus projetos  
 Por padrão, os projetos do VSIX somente geram pacotes VSIX, assemblies não. Portanto, você normalmente não implementar uma extensão de ferramentas do SharePoint em um projeto do VSIX. Geralmente, você trabalha com pelo menos dois projetos:  
  
-   Um projeto do VSIX.  
  
-   Um projeto de biblioteca de classe que implementa a sua extensão.  
  
 Também é possível trabalhar com projetos adicionais para certos tipos de extensões:  
  
-   Um projeto de biblioteca de classe que implementa comandos do SharePoint que são usados por sua extensão. Para uma explicação passo a passo que demonstre este cenário, consulte [passo a passo: estendendo o Gerenciador de servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Um projeto de modelo de Item de projeto que cria um modelo de item ou um modelo de projeto, se sua extensão define um novo tipo de item de projeto do SharePoint. Para uma explicação passo a passo que demonstre este cenário, consulte [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Um projeto de biblioteca de classe que implementa um assistente personalizado para um modelo de item ou um modelo de projeto, se sua extensão inclui um modelo. Para uma explicação passo a passo que demonstre este cenário, consulte [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Se você incluir todos os projetos na mesma solução do Visual Studio, você pode modificar o arquivo source.extension.vsixmanifest no projeto VSIX para incluir a saída de compilação dos projetos de biblioteca de classe.  
  
### <a name="editing-the-vsix-manifest"></a>Editar o manifesto do VSIX  
 Você deve editar o arquivo source.extension.vsixmanifest no projeto VSIX para incluir entradas para todos os itens que você deseja incluir em sua extensão. Quando você abre o arquivo source.extension.vsixmanifest no seu menu de atalho, o arquivo aparece em um designer que fornece uma interface de usuário para editar o XML no arquivo. Para obter mais informações, consulte [Designer de manifesto do VSIX](/visualstudio/extensibility/vsix-manifest-designer).  
  
 Você deve adicionar entradas para o arquivo source.extension.vsixmanifest para os seguintes itens:  
  
-   O assembly de extensão.  
  
-   O assembly que implementa comandos do SharePoint que são usados por sua extensão.  
  
-   Quaisquer modelos de projeto ou modelos de item que estão associados a sua extensão.  
  
-   Um assistente personalizado para um modelo que está associado a sua extensão.  
  
 Os procedimentos a seguir descrevem como adicionar entradas para o arquivo .vsixmanifest para cada um desses itens.  
  
##### <a name="to-include-the-extension-assembly"></a>Para incluir o assembly de extensão  
  
1.  No projeto VSIX, abra o menu de atalho para o arquivo source.extension.vsixmanifest e, em seguida, escolha **abrir**.  
  
     O arquivo é aberto no designer  
  
2.  Sobre o **ativos** guia do editor, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é aberta.  
  
3.  No **tipo** , escolha **Microsoft.VisualStudio.MefComponent**.  
  
4.  No **fonte** lista, execute uma das seguintes etapas:  
  
    -   Se o assembly de extensão é criado a partir de um projeto que está na mesma solução que o projeto VSIX, escolha **um projeto na solução atual**. No **projeto** , escolha o nome do projeto.  
  
    -   Se o assembly de extensão é incluído como um arquivo em seu projeto, escolha **arquivo no sistema de arquivos**. No **caminho** lista, digite o caminho completo para o arquivo de assembly de extensão ou use o **procurar** botão para localizar e escolha o arquivo de assembly.  
  
5.  Escolha o botão **OK**.  
  
##### <a name="to-include-a-sharepoint-command-assembly"></a>Para incluir um assembly de comando do SharePoint  
  
1.  No projeto VSIX, abra o menu de atalho para o arquivo source.extension.vsixmanifest e, em seguida, escolha o **abrir** botão.  
  
     O arquivo é aberto no designer.  
  
2.  No **ativos** seção do editor, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é aberta.  
  
3.  No **tipo** , digite **SharePoint.Commands.v4**.  
  
4.  No **fonte** lista, execute uma das seguintes etapas:  
  
    -   Se o assembly do comando é criado a partir de um projeto que está na mesma solução que o projeto VSIX, escolha **um projeto na solução atual**. No **projeto** , escolha o nome do projeto.  
  
    -   Se o assembly de comando é incluído como um arquivo em seu projeto, escolha **arquivo no sistema de arquivos**. No **caminho** lista, digite o caminho completo para o arquivo de assembly de extensão ou use o **procurar** botão para localizar e escolha o arquivo de assembly.  
  
5.  Escolha o botão **OK**.  
  
##### <a name="to-include-a-template-that-you-create"></a>Para incluir um modelo que você criar  
  
1.  No projeto VSIX, abra o menu de atalho para o arquivo source.extension.vsixmanifest e, em seguida, escolha o **abrir** botão.  
  
     O arquivo é aberto no designer.  
  
2.  No **ativos** seção do editor, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é aberta.  
  
3.  No **tipo** , escolha **Microsoft.VisualStudio.ProjectTemplate** ou **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  No **fonte** , escolha **um projeto na solução atual**.  
  
5.  No **projeto** lista, escolha o nome do projeto e, em seguida, escolha o **Okey** botão.  
  
6.  Em **Solution Explorer**, abra o menu de atalho para o seu projeto de modelo de projeto ou Item de modelo e, em seguida, escolha **descarregar projeto**.  
  
7.  Abra o menu de atalho para o nó do projeto novamente e, em seguida, escolha **editar***YourTemplateProjectName***. csproj** ou **editar**  *YourTemplateProjectName***. vbproj**.  
  
8.  Localize o seguinte `VSTemplate` elemento no arquivo de projeto.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Substitua este elemento XML a seguir.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     O `OutputSubPath` elemento Especifica pastas adicionais no caminho no qual o modelo de projeto é criado quando você compila o projeto. As pastas especificadas aqui Certifique-se de que o modelo de item estará disponível somente quando os clientes abrir o **adicionar novo projeto** caixa de diálogo caixa, expanda o **SharePoint** nó e, em seguida, escolha o **2010**  nó.  
  
10. Salve e feche o arquivo.  
  
11. Em **Solution Explorer**, abra o menu de atalho para o projeto de modelo de projeto ou Item de modelo e, em seguida, escolha **recarregar projeto**.  
  
##### <a name="to-include-a-template-that-you-create-manually"></a>Para incluir um modelo que você criar manualmente  
  
1.  No projeto VSIX, adicione uma nova pasta para o projeto para conter o modelo.  
  
2.  Nessa nova pasta, crie as seguintes subpastas e, em seguida, adicione o arquivo de modelo (. zip) para o *identificação de localidade* pasta.  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *ID de localidade*  
  
     *YourTemplateName*. zip  
  
     Por exemplo, se você tiver um modelo de item denominado ContosoCustomAction.zip que oferece suporte a localidade inglês (Estados Unidos), o caminho completo pode ser ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip.  
  
3.  Em **Solution Explorer**, escolha o arquivo de modelo (*YourTemplateName*. zip).  
  
4.  No **propriedades** janela, defina o **ação de compilação** propriedade **conteúdo**.  
  
5.  Abra o menu de atalho para o arquivo source.extension.vsixmanifest e, em seguida, escolha **abrir**.  
  
     O arquivo é aberto no designer.  
  
6.  No **ativos** seção do editor, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é aberta.  
  
7.  No **tipo** , escolha **Microsoft.VisualStudio.ItemTemplate** ou **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  No **fonte** , escolha **arquivo no sistema de arquivos**.  
  
9. No **caminho** campo, digite o caminho completo para o assembly (por exemplo, **ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip**, ou use o **procurar**botão para localizar e selecione o assembly e, em seguida, escolha o **Okey** botão.  
  
##### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Para incluir um Assistente para um modelo de projeto ou o modelo de item  
  
1.  No projeto VSIX, abra o menu de atalho para o arquivo source.extension.vsixmanifest e, em seguida, escolha **abrir**.  
  
     O arquivo é aberto no designer.  
  
2.  No **ativos** seção do editor, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é aberta.  
  
3.  No **tipo** , escolha **Microsoft.VisualStudio.Assembly**.  
  
4.  No **fonte** lista, execute uma das seguintes etapas:  
  
    -   Se o assembly do assistente é criado a partir de um projeto que está na mesma solução que o projeto VSIX, escolha **um projeto na solução atual**. No **projeto** , escolha o nome do projeto.  
  
    -   Se o assembly do assistente está incluído como um arquivo em seu projeto, escolha **arquivo no sistema de arquivos**. No **caminho** campo, digite o caminho completo para o arquivo de assembly ou use o **procurar** botão para localizar e escolha o assembly.  
  
5.  Escolha o botão **OK**.  
  
### <a name="related-walkthroughs"></a>Explicações passo a passo relacionada  
 A tabela a seguir lista as instruções passo a passo que demonstre como usar um projeto do VSIX para implantar diferentes tipos de extensões de ferramentas do SharePoint.  
  
|Tipo de extensão|Explicações passo a passo relacionada|  
|--------------------|--------------------------|  
|Uma extensão que inclui apenas o assembly de extensão|[Instruções passo a passo: estendendo um tipo de item do projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Instruções passo a passo: criando uma extensão de projeto do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Instruções passo a passo: chamando o modelo do objeto de cliente do SharePoint em uma extensão do Gerenciador de Servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Uma extensão que inclui comandos do SharePoint|[Instruções passo a passo: criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Instruções passo a passo: estendendo o Gerenciador de Servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Instruções passo a passo: criando um item de projeto da coluna do site com um modelo de projeto, Parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Uma extensão que inclui um modelo do Visual Studio|[Instruções passo a passo: criando um item de projeto de ação personalizado com um modelo de item, Parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Instruções passo a passo: criando um item de projeto da coluna do site com um modelo de projeto, Parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Uma extensão que inclui um Assistente de modelo|[Instruções passo a passo: criando um item de projeto de ação personalizado com um modelo de item, Parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Instruções passo a passo: criando um item de projeto da coluna do site com um modelo de projeto, Parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## <a name="creating-vsix-packages-manually"></a>Criando pacotes VSIX manualmente  
 Se você quiser criar manualmente o pacote do VSIX para a sua extensão de ferramentas do SharePoint, execute as seguintes etapas:  
  
1.  Crie o arquivo extension.vsixmanifest e o arquivo. XML [Content_Types] em uma nova pasta. Para obter mais informações, consulte [Anatomia de um pacote do VSIX](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
2.  No Windows Explorer, clique na pasta que contém os dois arquivos XML, clique em Enviar para e, em seguida, clique em pasta compactada (zipada). Renomeie o arquivo. zip resultante para Filename.vsix, onde o nome do arquivo é o nome do arquivo redistribuível que instala o pacote.  
  
3.  Adicione seu assembly de extensão para o pacote do VSIX. Se sua extensão de incluir um comando do SharePoint, também adicione o assembly que implementa o comando do SharePoint para o pacote do VSIX.  
  
4.  Modifique o arquivo extension.vsixmanifest:  
  
    -   Adicionar um `Microsoft.VisualStudio.MefComponent` elemento sob o `Assets` elemento e, em seguida, defina o valor do novo elemento para o caminho relativo do assembly que implementa a extensão do pacote VSIX. Para obter mais informações, consulte [MEFComponent Element (esquema de VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Se sua extensão inclui um comando do SharePoint que chama o modelo de objeto de servidor para o SharePoint, adicione um `Microsoft.VisualStudio.Assembly` elemento sob o `Assets` elemento. Defina o valor do novo elemento para o caminho relativo do assembly que implementa o comando do SharePoint no pacote do VSIX. Para obter mais informações, consulte [elemento ativo (esquema VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Se sua extensão inclui um modelo de projeto ou o modelo de item, adicione um `ProjectTemplate` ou `ItemTemplate` elemento sob o `Assets` elemento. Defina o valor do novo elemento para o caminho relativo da pasta que contém o modelo no pacote do VSIX. Para obter mais informações, consulte [ProjectTemplate Element (esquema de VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1) e [ItemTemplate Element (esquema de VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Se sua extensão inclui um assistente personalizado para um modelo de item ou o modelo de projeto, adicione um `Assembly` elemento sob o `Assets` elemento. Defina o valor do novo elemento para o caminho relativo do assembly no pacote VSIX e defina o `AssemblyName` de atributo para o nome de assembly completo (incluindo a versão, cultura e token de chave pública). Para obter mais informações, consulte [(esquema VSX) do elemento de dependência](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o conteúdo de um arquivo de extension.vsixmanifest para uma extensão de ferramentas do SharePoint. A extensão é implementada em um assembly chamado Contoso.ProjectExtension.dll. A extensão inclui um assembly de comando do SharePoint que é chamado Contoso.ExtensionCommands.dll e um modelo de item em uma pasta denominada **ItemTemplates** no pacote do VSIX. Este exemplo presume que ambos os assemblies estão na mesma pasta que o arquivo extension.vsixmanifest no pacote do VSIX.  
  
```  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [A chamada para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Depurando extensões para as Ferramentas do SharePoint no Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  