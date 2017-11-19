---
title: "Passo a passo: Criando uma etapa de implantação para projetos SharePoint | Microsoft Docs"
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
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b7375071522ea59c9c00a5fa94277a3817438d25
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects"></a>Instruções passo a passo: criando uma etapa de implantação para projetos SharePoint
  Quando você implanta um projeto do SharePoint, o Visual Studio executa uma série de etapas de implantação em uma ordem específica. O Visual Studio inclui várias etapas de implantação interna, mas você também pode criar seus próprios.  
  
 Este passo a passo, você criará uma etapa de implantação personalizada para atualizar soluções em um servidor que está executando o SharePoint. O Visual Studio inclui etapas de implantação interna para muitas tarefas, tal cancelamento ou a adição de soluções, mas não inclui uma etapa de implantação de atualização de soluções. Por padrão, quando você implanta uma solução do SharePoint, o Visual Studio primeiro retira a solução (se já estiver implantado) e, em seguida, reimplantar a solução inteira. Para obter mais informações sobre as etapas de implantação interna, consulte [atualizar os pacotes de solução do SharePoint, publicação e implantação](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando uma extensão do Visual Studio que executa duas tarefas principais:  
  
    -   A extensão define uma etapa de implantação personalizada para atualizar soluções do SharePoint.  
  
    -   A extensão cria uma extensão de projeto que define uma nova configuração de implantação, que é um conjunto de etapas de implantação que são executadas para um determinado projeto. A nova configuração de implantação inclui a etapa de implantação personalizada e várias etapas de implantação interna.  
  
-   Criar dois comandos do SharePoint personalizados que chama o assembly de extensão. Comandos do SharePoint são métodos que podem ser chamados por assemblies de extensão para usar APIs no modelo de objeto de servidor do SharePoint. Para obter mais informações, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Criando um pacote de extensão de Visual Studio (VSIX) para implantar ambos os assemblies.  
  
-   Testar a nova etapa de implantação.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisará dos seguintes componentes no computador de desenvolvimento para concluir este passo a passo:  
  
-   Edições com suporte do Windows, o SharePoint e o Visual Studio. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   O SDK do Visual Studio. Este passo a passo usa o **projeto VSIX** modelo no SDK para criar um pacote do VSIX para implantar a extensão. Para obter mais informações, consulte [estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conhecimento sobre os conceitos a seguir é útil, mas não necessário para concluir o passo a passo:  
  
-   Usando o modelo de objeto do servidor do SharePoint. Para obter mais informações, consulte [usando o modelo de objeto do lado do servidor do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Soluções do SharePoint. Para obter mais informações, consulte [visão geral das soluções](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
-   Atualizando soluções do SharePoint. Para obter mais informações, consulte [atualização de uma solução](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
 Para concluir este passo a passo, você deve criar três projetos:  
  
-   Um projeto do VSIX para criar o pacote do VSIX para implantar a extensão.  
  
-   Um projeto de biblioteca de classe que implementa a extensão. Este projeto deve usar o .NET Framework 4.5.  
  
-   Um projeto de biblioteca de classe que define os comandos do SharePoint personalizados. Este projeto deve usar o .NET Framework 3.5.  
  
 Criando projetos para iniciar o passo a passo.  
  
#### <a name="to-create-the-vsix-project"></a>Para criar o projeto do VSIX  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
3.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **extensibilidade** nó.  
  
    > [!NOTE]  
    >  O **extensibilidade** nó estará disponível somente se você instalar o SDK do Visual Studio. Para obter mais informações, consulte a seção pré-requisitos neste tópico.  
  
4.  Na parte superior da caixa de diálogo, escolha **.NET Framework 4.5** na lista de versões do .NET Framework.  
  
5.  Escolha o **projeto VSIX** modelo, nomeie o projeto **UpgradeDeploymentStep**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o **UpgradeDeploymentStep** projeto **Gerenciador de soluções**.  
  
#### <a name="to-create-the-extension-project"></a>Para criar o projeto de extensão  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução UpgradeDeploymentStep, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **Windows** nó.  
  
3.  Na parte superior da caixa de diálogo, escolha **.NET Framework 4.5** na lista de versões do .NET Framework.  
  
4.  Escolha o **biblioteca de classes** modelo de projeto, nomeie o projeto **DeploymentStepExtension**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o **DeploymentStepExtension** projeto à solução e abre o arquivo de código Class1 padrão.  
  
5.  Exclua o arquivo de código Class1 do projeto.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Para criar o projeto de comando do SharePoint  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução UpgradeDeploymentStep, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic**e, em seguida, escolha o **Windows** nó.  
  
3.  Na parte superior da caixa de diálogo, escolha **.NET Framework 3.5** na lista de versões do .NET Framework.  
  
4.  Escolha o **biblioteca de classes** modelo de projeto, nomeie o projeto **SharePointCommands**e, em seguida, escolha o **Okey** botão.  
  
     O Visual Studio adiciona o **SharePointCommands** projeto à solução e abre o arquivo de código Class1 padrão.  
  
5.  Exclua o arquivo de código Class1 do projeto.  
  
## <a name="configuring-the-projects"></a>Configurando projetos  
 Antes de escrever código para criar a etapa de implantação personalizada, você deve adicionar arquivos de código e referências de assembly, e você deve configurar os projetos.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Configurar o projeto DeploymentStepExtension  
  
1.  No **DeploymentStepExtension** de projeto, adicione dois arquivos de código que têm os seguintes nomes:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Abra o menu de atalho do projeto DeploymentStepExtension e, em seguida, escolha **adicionar referência**.  
  
3.  Sobre o **Framework** guia, marque a caixa de seleção para o assembly System.ComponentModel.Composition.  
  
4.  Sobre o **extensões** guia, marque a caixa de seleção para o assembly Microsoft.VisualStudio.SharePoint e, em seguida, escolha o **Okey** botão.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Configurar o projeto SharePointCommands  
  
1.  No **SharePointCommands** de projeto, adicione um arquivo de código que é chamado de comandos.  
  
2.  Em **Solution Explorer**, abra o menu de atalho no **SharePointCommands** nó do projeto e escolha **adicionar referência**.  
  
3.  Sobre o **extensões** guia, marque as caixas de seleção para os seguintes assemblies e, em seguida, clique em escolher o **Okey** botão  
  
    -   Microsoft. SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="defining-the-custom-deployment-step"></a>Definindo a etapa de implantação personalizada  
 Crie uma classe que define a etapa da implantação de atualização. Para definir a etapa da implantação, a classe implementa o <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interface. Implemente esta interface sempre que você deseja definir uma etapa de implantação.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Para definir a etapa de implantação personalizada  
  
1.  No **DeploymentStepExtension** de projeto, abra o arquivo de código UpgradeStep e, em seguida, cole o seguinte código para ele.  
  
    > [!NOTE]  
    >  Depois que você adicione esse código, o projeto terá alguns erros de compilação, mas vai desaparecer quando você adiciona o código em etapas posteriores.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="creating-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Criar uma configuração de implantação que inclui a etapa de implantação personalizada  
 Crie uma extensão de projeto para a nova configuração de implantação, que inclui várias etapas de implantação interna e a nova etapa de implantação da atualização. Criando essa extensão, você ajudar os desenvolvedores do SharePoint para usar a etapa da implantação de atualização em projetos do SharePoint.  
  
 Para criar a configuração de implantação, a classe implementa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Implemente esta interface sempre que você deseja criar uma extensão de projeto do SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Para criar a configuração de implantação  
  
1.  
  
2.  No **DeploymentStepExtension** de projeto, abra o arquivo de código DeploymentConfigurationExtension e, em seguida, cole o seguinte código para ele.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Criando os comandos do SharePoint personalizado  
 Crie dois comandos personalizados que chamam o modelo de objeto do servidor do SharePoint. Um comando determina se uma solução já está implantada; outro comando atualiza uma solução.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Para definir os comandos do SharePoint  
  
1.  No **SharePointCommands** de projeto, abra o arquivo de código de comandos e, em seguida, cole o seguinte código para ele.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Nesse ponto no passo a passo, todo o código para a etapa de implantação personalizada e os comandos do SharePoint estão agora em projetos. Criá-las para certificar-se de que eles compilar sem erros.  
  
#### <a name="to-build-the-projects"></a>Para criar os projetos  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **DeploymentStepExtension** do projeto e, em seguida, escolha **criar**.  
  
2.  Abra o menu de atalho para o **SharePointCommands** do projeto e, em seguida, escolha **criar**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Criando um pacote do VSIX para implantar a extensão  
 Para implantar a extensão, use o projeto do VSIX em sua solução para criar um pacote do VSIX. Primeiro, configure o pacote VSIX, modificando o arquivo source.extension.vsixmanifest no projeto do VSIX. Crie o pacote do VSIX por compilar a solução.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Para configurar e criar o pacote VSIX  
  
1.  Em **Solution Explorer**, no **UpgradeDeploymentStep** de projeto, abra o menu de atalho para o **source.extension.vsixmanifest** file e, em seguida, escolha  **Abra**.  
  
     O Visual Studio abrirá o arquivo no editor de manifesto. O arquivo source.extension.vsixmanifest é a base para o arquivo extension.vsixmanifest que necessitam de todos os pacotes VSIX. Para obter mais informações sobre esse arquivo, consulte [1.0 referência do esquema de extensão de VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  No **nome do produto** , digite **atualizar a etapa de implantação para projetos SharePoint**.  
  
3.  No **autor** , digite **Contoso**.  
  
4.  No **descrição** , digite **fornece uma etapa de implantação de atualização personalizada que pode ser usada em projetos SharePoint**.  
  
5.  No **ativos** guia do editor, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
6.  No **tipo** , escolha **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Esse valor corresponde do `MefComponent` elemento no arquivo extension.vsixmanifest. Este elemento Especifica o nome de um assembly de extensão do pacote VSIX. Para obter mais informações, consulte [MEFComponent Element (esquema de VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  No **fonte** , escolha **um projeto na solução atual**.  
  
8.  No **projeto** , escolha **DeploymentStepExtension**e, em seguida, escolha o **Okey** botão.  
  
9. No editor de manifesto, escolha o **novo** novamente.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
10. No **tipo** , digite **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Este elemento Especifica uma extensão personalizada que você deseja incluir na extensão do Visual Studio. Para obter mais informações, consulte [elemento ativo (esquema VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. No **fonte** , escolha **um projeto na solução atual**.  
  
12. No **projeto** , escolha **SharePointCommands**e, em seguida, escolha o **Okey** botão.  
  
13. Na barra de menus, escolha **criar**, **compilar solução**e, em seguida, certifique-se de que a solução compilado sem erros.  
  
14. Certifique-se de que a pasta de saída de compilação do projeto UpgradeDeploymentStep agora contém o arquivo UpgradeDeploymentStep.vsix.  
  
     Por padrão, a pasta de saída de compilação é o. pasta \bin\debug sob a pasta que contém o arquivo de projeto.  
  
## <a name="preparing-to-test-the-upgrade-deployment-step"></a>Preparando-se para a etapa da implantação de atualização de teste  
 Para testar a etapa da implantação de atualização, você deve primeiro implantar uma solução de exemplo para o site do SharePoint. Iniciar depuração a extensão na instância experimental do Visual Studio. Em seguida, criar uma definição de lista e a instância de lista a ser usada para testar a etapa da implantação e, em seguida, implantá-los para o site do SharePoint. Em seguida, modifique a definição de lista e a instância de lista e reimplantá-los para demonstrar como o processo de implantação padrão substitui soluções no site do SharePoint.  
  
 Posteriormente neste passo a passo, você modificará a definição de lista e a instância de lista e, em seguida, você poderá atualizá-los no site do SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Para iniciar a depuração de extensão  
  
1.  Reinicie o Visual Studio com credenciais administrativas e, em seguida, abra a solução de UpgradeDeploymentStep.  
  
2.  No projeto DeploymentStepExtension, abra o arquivo de código UpgradeStep e, em seguida, adicione um ponto de interrupção para a primeira linha do código no `CanExecute` e `Execute` métodos.  
  
3.  Iniciar a depuração, escolhendo a tecla F5 ou, na barra de menus, escolhendo **depurar**, **iniciar depuração**.  
  
4.  Visual Studio instala a extensão para %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade etapa da implantação do SharePoint Projects\1.0 e inicia uma instância experimental do Visual Studio. Você testará a etapa da implantação de atualização nesta instância do Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Para criar um projeto do SharePoint com uma definição de lista e uma instância de lista  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** nó ou o **Visual Basic** nó, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
3.  Na parte superior da caixa de diálogo, certifique-se de que **.NET Framework 3.5** aparece na lista de versões do .NET Framework.  
  
     Projetos para [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exigem essa versão do .NET Framework.  
  
4.  Na lista de modelos de projeto, escolha **projeto do SharePoint 2010**, nomeie o projeto **EmployeesListDefinition**e, em seguida, escolha o **Okey** botão.  
  
5.  No **Assistente de personalização do SharePoint**, insira a URL do site que você deseja usar para depuração.  
  
6.  Em **o que é o nível de confiança para essa solução do SharePoint**, escolha o **implantar como uma solução de farm** botão de opção.  
  
    > [!NOTE]  
    >  A etapa da implantação de atualização não oferece suporte a soluções de área restrita.  
  
7.  Escolha o **concluir** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]cria o projeto EmployeesListDefinition.  
  
8.  Abra o menu de atalho para o projeto EmployeesListDefinition, escolha **adicionar**e, em seguida, escolha **Novo Item**.  
  
9. No **Adicionar Novo Item - EmployeesListDefinition** caixa de diálogo caixa, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
10. Escolha o **lista** item modelo, o nome do item **lista de funcionários**e, em seguida, escolha o **adicionar** botão.  
  
     O Assistente de personalização do SharePoint é exibido  
  
11. Sobre o **escolha as configurações da lista** página, verifique as configurações a seguir e, em seguida, escolha o **concluir** botão:  
  
    1.  **Lista de funcionários** aparece no **que nome você deseja exibir para sua lista?** caixa.  
  
    2.  O **criar uma lista personalizada com base em:** botão de opção é escolhido.  
  
    3.  **Padrão (em branco)** é escolhido no **criar uma lista personalizada com base em:** lista.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]cria o item de lista de funcionários com uma coluna de título e uma única instância vazia e abre o Designer da lista.  
  
12. No Designer de lista, no **colunas** guia, escolha o **digite um nome de coluna nova ou existente** de linha e, em seguida, adicione as seguintes colunas no **nome da coluna de exibição** lista:  
  
    1.  Primeiro nome  
  
    2.  Empresa  
  
    3.  Telefone comercial  
  
    4.  Email  
  
13. Salvar todos os arquivos e, em seguida, feche o Designer de lista.  
  
14. Em **Solution Explorer**, expanda o **lista de funcionários** nó e, em seguida, expanda o **instância de lista de funcionários** nó filho.  
  
15. No arquivo Elements, substitua o padrão XML no arquivo pelo XML a seguir. Esse XML altera o nome da lista para **funcionários** e adiciona informações de um funcionário que possui chamada Jim Hance.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Salve e feche o arquivo Elements.  
  
17. Abra o menu de atalho para o projeto EmployeesListDefinition e, em seguida, escolha **abrir** ou **propriedades**.  
  
     Abre o Designer de propriedades.  
  
18. Sobre o **SharePoint** guia, desmarque o **cancele automaticamente após a depuração** caixa de seleção e, em seguida, salvar as propriedades.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Para implantar a definição de lista e a instância de lista  
  
1.  Em **Solution Explorer**, escolha o **EmployeesListDefinition** nó do projeto.  
  
2.  No **propriedades** janela, verifique se o **configuração de implantação ativa** está definida como **padrão**.  
  
3.  Pressione a tecla F5 ou, na barra de menus, escolha **depurar**, **iniciar depuração**.  
  
4.  Verifique se o projeto é compilado com êxito, que o navegador da web abre o site do SharePoint, que o **lista** item na barra Início Rápido inclui o novo **funcionários** lista e que o  **Os funcionários** lista inclui a entrada para Jim Hance.  
  
5.  Feche o navegador da web.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Para modificar a definição de lista e a instância de lista e reimplantá-los  
  
1.  No projeto EmployeesListDefinition, abra o arquivo de Elements. XML que é um filho de **instância de lista de funcionários** item de projeto.  
  
2.  Remover o `Data` elemento e seus filhos para remover a entrada de Jim Hance da lista.  
  
     Quando você terminar, o arquivo deve conter o seguinte XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Salve e feche o arquivo Elements.  
  
4.  Abra o menu de atalho para o **lista de funcionários** item de projeto e escolha **abrir** ou **propriedades**.  
  
5.  No Designer de lista, escolha o **exibições** guia.  
  
6.  No **colunas selecionadas** , escolha **anexos**e, em seguida, escolha o < chave para mover a coluna para o **colunas disponíveis** lista.  
  
7.  Repita a etapa anterior para mover o **telefone comercial** coluna a partir de **colunas selecionadas** lista para o **colunas disponíveis** lista.  
  
     Essa ação remove esses campos do modo de exibição padrão de **funcionários** lista no site do SharePoint.  
  
8.  Iniciar a depuração, escolhendo a tecla F5 ou, na barra de menus, escolhendo **depurar**, **iniciar depuração**.  
  
9. Verifique o **conflitos de implantação** caixa de diálogo é exibida.  
  
     Essa caixa de diálogo aparece quando o Visual Studio tenta implantar uma solução (a instância de lista) para um site do SharePoint ao qual essa solução já foi implantada. Essa caixa de diálogo não aparecerá quando você executar a etapa da implantação de atualização mais tarde neste passo a passo.  
  
10. No **conflitos de implantação** caixa de diálogo caixa, escolha o **resolver automaticamente** botão de opção.  
  
     O Visual Studio exclui a instância de lista no site do SharePoint, implanta o item de lista no projeto e, em seguida, abre o site do SharePoint.  
  
11. No **lista** seção da barra de início rápido, escolha o **funcionários** lista e, em seguida, verifique se os seguintes detalhes:  
  
    -   O **anexos** e **telefone residencial** colunas não aparecem neste modo de exibição da lista.  
  
    -   A lista está vazia. Quando você usou o **padrão** configuração de implantação para reimplantar a solução, o **funcionários** lista foi substituída com a nova lista vazia em seu projeto.  
  
## <a name="testing-the-deployment-step"></a>A etapa de implantação de teste  
 Agora você está pronto para testar a etapa da implantação de atualização. Primeiro, adicione um item para a instância de lista do SharePoint. Em seguida, altere a definição de lista e a instância de lista, atualizá-los no site do SharePoint e confirme que a etapa da implantação de atualização não substitui o novo item.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Para adicionar manualmente um item à lista  
  
1.  Na faixa de opções no site do SharePoint, sob o **lista ferramentas** guia, escolha o **itens** guia.  
  
2.  No **novo** de grupo, escolha **Novo Item**.  
  
     Como alternativa, você pode escolher o **adicionar novo item** link na lista de itens em si.  
  
3.  No **funcionários - Novo Item** janela, no **título** , digite **gerente de instalações**.  
  
4.  No **nome** , digite **Andy**.  
  
5.  No **empresa** , digite **Contoso**.  
  
6.  Escolha o **salvar** botão, verifique se o novo item aparece na lista e, em seguida, feche o navegador da web.  
  
     Posteriormente neste passo a passo, você usará este item para verificar que a etapa da implantação de atualização não substitui o conteúdo desta lista.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Para testar a etapa da implantação de atualização  
  
1.  Na instância experimental do Visual Studio, no **Solution Explorer**, abra o menu de atalho para o **EmployeesListDefinition** nó do projeto e escolha **propriedades**.  
  
     O Editor de propriedades/Designer é aberto.  
  
2.  No **SharePoint** guia, defina o **configuração de implantação ativa** propriedade **atualizar**.  
  
     Essa configuração de implantação personalizada inclui a nova etapa de implantação da atualização.  
  
3.  Abra o menu de atalho para o **lista de funcionários** item de projeto e escolha **propriedades** ou **abrir**.  
  
     O Editor de propriedades/Designer é aberto.  
  
4.  No **exibições** guia, escolha o **email** coluna e, em seguida, escolha o  **<**  chave para mover a coluna do **selecionado colunas**lista para o **colunas disponíveis** lista.  
  
     Essa ação remove esses campos do modo de exibição padrão de **funcionários** lista no site do SharePoint.  
  
5.  Iniciar a depuração, escolhendo a tecla F5 ou, na barra de menus, escolhendo **depurar**, **iniciar depuração**.  
  
6.  Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definiu anteriormente no `CanExecute` método.  
  
7.  Pressione a tecla F5 novamente ou, na barra de menus, escolha **depurar**, **continuar**.  
  
8.  Verifique se que o código para no ponto de interrupção que você definiu anteriormente no `Execute` método.  
  
9. Pressione a tecla F5 ou, na barra de menus, escolha **depurar**, **continuar** uma última vez.  
  
     O navegador da web abre o site do SharePoint.  
  
10. No **lista** seção da área de início rápido, escolha o **funcionários** lista e, em seguida, verifique se os seguintes detalhes:  
  
    -   O item que você adicionou manualmente anteriormente (por Andy, o Gerenciador de recursos) é ainda na lista.  
  
    -   O **telefone comercial** e **endereço de email** colunas não aparecem neste modo de exibição da lista.  
  
     O **atualização** modifica de configuração de implantação existente **funcionários** instância de lista no site do SharePoint. Se você usou o **padrão** configuração de implantação em vez do **atualização** configuração, você encontra um conflito de implantação. O Visual Studio deve resolver o conflito, substituindo o **funcionários** lista e o item de Andy, o Gerenciador de recursos, serão excluídos.  
  
## <a name="cleaning-up-the-development-computer"></a>Limpando o computador de desenvolvimento  
 Depois de concluir o teste a etapa da implantação de atualização, remova a instância de lista e a definição de lista do site do SharePoint e remover a extensão de etapa de implantação do Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Para remover a instância de lista do site do SharePoint  
  
1.  Abra o **funcionários** lista no site do SharePoint, se a lista não estiver aberta.  
  
2.  Na faixa de opções no site do SharePoint, escolha o **lista ferramentas** guia e, em seguida, escolha o **lista** guia.  
  
3.  No **configurações** de grupo, escolha o **as configurações da lista** item.  
  
4.  Em **permissões e gerenciamento**, escolha o **excluir essa lista** de comando, escolha **Okey** para confirmar que você deseja enviar a lista para a Lixeira e, em seguida, feche a web Navegador.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Para remover a definição de lista do site do SharePoint  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **criar**, **Retract**.  
  
     O Visual Studio retira a definição de lista do site do SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar a extensão  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
     A caixa de diálogo **Extensões e Atualizações** é aberta.  
  
2.  Na lista de extensões, escolha **atualizar a etapa de implantação para projetos SharePoint**e, em seguida, escolha o **desinstalação** comando.  
  
3.  Na caixa de diálogo que aparece, escolha **Sim** para confirmar que você deseja desinstalar a extensão e, em seguida, escolha **reiniciar agora** para concluir a desinstalação.  
  
4.  Feche ambas as instâncias do Visual Studio (a instância experimental e a instância do Visual Studio, em que a solução UpgradeDeploymentStep estiver aberta).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  