---
title: "Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 2 | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 55794f7976e90e34ba24654400f755de9244e13e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2"></a>Instruções passo a passo: criando um item de projeto de ação com um modelo de item, parte 2
  Depois de definir um tipo personalizado do item de projeto do SharePoint e associá-lo a um modelo de item no Visual Studio, você também poderá fornecer um Assistente para o modelo. Você pode usar o Assistente para coletar informações de usuários quando eles usam o modelo para adicionar uma nova instância do item de projeto para um projeto. As informações que você coletar podem ser usadas para inicializar o item de projeto.  
  
 Neste passo a passo, você adicionará um Assistente para o item de projeto de ação personalizada que é demonstrado [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Quando um usuário adiciona um item de projeto de ação personalizada para um projeto do SharePoint, o assistente coleta informações sobre a ação personalizada (como o local e a URL para navegar quando um usuário final escolhe-lo) e adiciona informações ao arquivo Elements no novo item de projeto.  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando um Assistente para um tipo de item de projeto do SharePoint personalizado que está associado um modelo de item.  
  
-   Definindo um assistente personalizado da interface do usuário que se parece com os assistentes internos para itens de projeto do SharePoint no Visual Studio.  
  
-   Usando parâmetros substituíveis para inicializar os arquivos de projeto do SharePoint com os dados coletados no assistente.  
  
-   Depuração e teste o assistente.  
  
> [!NOTE]  
>  Você pode baixar um exemplo que contém os projetos concluídos, código e outros arquivos para este passo a passo no seguinte local: [arquivos de projeto para orientações de extensibilidade de ferramentas do SharePoint](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para executar este passo a passo, você deve primeiro criar a solução CustomActionProjectItem Concluindo [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Você também precisará dos seguintes componentes no computador de desenvolvimento para concluir este passo a passo:  
  
-   Edições com suporte do Windows, o SharePoint e o Visual Studio. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   O SDK do Visual Studio. Este passo a passo usa o **projeto VSIX** modelo no SDK para criar um pacote do VSIX para implantar o item de projeto. Para obter mais informações, consulte [estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conhecimento sobre os conceitos a seguir é útil, mas não necessário para concluir o passo a passo:  
  
-   Assistentes para modelos de projeto e item no Visual Studio. Para obter mais informações, consulte [como: usar assistentes com modelos de projeto](../extensibility/how-to-use-wizards-with-project-templates.md) e <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.  
  
-   Ações personalizadas no SharePoint. Para obter mais informações, consulte [ação personalizada](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="creating-the-wizard-project"></a>Criando o projeto de Assistente  
 Para concluir este passo a passo, você deve adicionar um projeto à solução CustomActionProjectItem que você criou na [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Você implementará o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface e defina o Assistente de interface de usuário neste projeto.  
  
#### <a name="to-create-the-wizard-project"></a>Para criar o projeto de Assistente  
  
1.  No Visual Studio, abra a solução CustomActionProjectItem  
  
2.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
3.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **Windows** nó.  
  
4.  Na parte superior do **novo projeto** caixa de diálogo caixa, certifique-se de que **.NET Framework 4.5** for escolhido na lista de versões do .NET Framework.  
  
5.  Escolha o **biblioteca de controle de usuário do WPF** modelo de projeto, nomeie o projeto **ItemTemplateWizard**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o **ItemTemplateWizard** projeto à solução.  
  
6.  Exclua o item de UserControl1 do projeto.  
  
## <a name="configuring-the-wizard-project"></a>Configurando o projeto de Assistente  
 Antes de criar o assistente, você deve adicionar uma janela do Windows Presentation Foundation (WPF), um arquivo de código e referências de assembly para o projeto.  
  
#### <a name="to-configure-the-wizard-project"></a>Configurar o projeto de Assistente  
  
1.  Em **Solution Explorer**, abra o menu de atalho do **ItemTemplateWizard** nó do projeto e escolha **propriedades**.  
  
2.  No **Project Designer**, certifique-se de que a estrutura de destino é definida como o .NET Framework 4.5.  
  
     Para projetos do Visual c#, você pode definir esse valor no **aplicativo** guia. Para projetos do Visual Basic, você pode definir esse valor no **compilar** guia. Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  No **ItemTemplateWizard** de projeto, adicione um **janela (WPF)** item ao projeto e, em seguida, o nome do item **WizardWindow**.  
  
4.  Adicione os dois arquivos de código que são nomeados CustomActionWizard e cadeias de caracteres.  
  
5.  Abra o menu de atalho para o **ItemTemplateWizard** do projeto e, em seguida, escolha **adicionar referência**.  
  
6.  No **Gerenciador de referências - ItemTemplateWizard** caixa de diálogo de **Assemblies** nó, escolha o **extensões** nó.  
  
7.  Selecione as caixas de seleção ao lado de assemblies a seguir e, em seguida, escolha o **Okey** botão:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  Em **Solution Explorer**, no **referências** pasta do projeto ItemTemplateWizard, escolha o **EnvDTE** referência.  
  
9. No **propriedades** janela, altere o valor da **Embed Interop Types** propriedade **False**.  
  
## <a name="defining-the-default-location-and-id-strings-for-custom-actions"></a>Definindo o local padrão e cadeias de caracteres de identificação de ações personalizadas  
 Cada ação personalizada tem um local e uma ID que é especificado no `GroupID` e `Location` atributos do `CustomAction` elemento no arquivo Elements. Nesta etapa, você definirá algumas das cadeias de caracteres válidas para esses atributos no projeto ItemTemplateWizard. Quando você concluir este passo a passo, essas cadeias de caracteres são gravadas no arquivo Elements no item de projeto de ação personalizada quando os usuários no Assistente para especificar um local e uma ID.  
  
 Para simplificar, este exemplo dá suporte a apenas um subconjunto das IDs e os locais de padrão disponíveis. Para obter uma lista completa, consulte [locais de ação personalizada padrão e IDs de](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Para definir o local padrão e cadeias de caracteres de ID  
  
1.  Abrir.  
  
2.  No **ItemTemplateWizard** de projeto, substitua o código no arquivo de código de cadeias de caracteres com o código a seguir.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="creating-the-wizard-ui"></a>Criando o Assistente de interface do usuário  
 Adicionar o XAML para definir a interface do usuário do assistente e adicionar código para vincular alguns dos controles no Assistente para as cadeias de caracteres de ID. O assistente que você criar se parece com o Assistente interno para projetos do SharePoint no Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Para criar o Assistente de interface do usuário  
  
1.  No **ItemTemplateWizard** de projeto, abra o menu de atalho para o **WizardWindow.xaml** file e, em seguida, escolha **abrir** para abrir a janela no designer.  
  
2.  No modo de exibição XAML, substitua o XAML atual com o XAML a seguir. O XAML define uma interface do usuário que inclui um título, controles para especificar o comportamento da ação personalizada e botões de navegação na parte inferior da janela.  
  
    > [!NOTE]  
    >  O projeto terá alguns erros de compilação depois de adicionar este código. Esses erros desaparecerá quando você adiciona o código em etapas posteriores.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  A janela que é criada neste XAML é derivada de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe base. Quando você adiciona uma caixa de diálogo personalizada do WPF para o Visual Studio, é recomendável que você deriva a caixa de diálogo desta classe ter um estilo consistente com outras caixas de diálogo no Visual Studio e para evitar problemas que possam ocorrer com caixas de diálogo modal. Para obter mais informações, consulte [criando e gerenciando caixas de diálogo modais](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Se você estiver desenvolvendo um projeto do Visual Basic, remova o `ItemTemplateWizard` namespace do `WizardWindow` nome da classe a `x:Class` atributo do `Window` elemento. Esse elemento é na primeira linha do XAML. Quando terminar, a primeira linha deve se parecer com o código a seguir:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  No arquivo de code-behind para o arquivo WizardWindow.xaml, substitua o código atual com o código a seguir.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implementing-the-wizard"></a>Implementando o Assistente  
 Definir a funcionalidade do assistente Implementando o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.  
  
#### <a name="to-implement-the-wizard"></a>Para implementar o Assistente  
  
1.  No **ItemTemplateWizard** projeto, abra o **CustomActionWizard** arquivo de código e, em seguida, substitua o código atual nesse arquivo com o código a seguir:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Nesse ponto no passo a passo, todo o código para que o assistente está agora no projeto. Crie o projeto para certificar-se de que ele foi compilado sem erros.  
  
#### <a name="to-build-your-project"></a>Para compilar o projeto  
  
1.  Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
## <a name="associating-the-wizard-with-the-item-template"></a>Associando o Assistente de modelo de Item  
 Agora que você implementou o assistente, você deve associá-lo com o **ação personalizada** modelo de item por três etapas principais:  
  
1.  Assine o assembly de assistente com um nome forte.  
  
2.  Obter token de chave pública para o assembly do assistente.  
  
3.  Adicione uma referência ao assembly do assistente no arquivo. vstemplate para o **ação personalizada** modelo de item.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Para assinar o assembly de assistente com um nome forte  
  
1.  Em **Solution Explorer**, abra o menu de atalho do **ItemTemplateWizard** nó do projeto e escolha **propriedades**.  
  
2.  Sobre o **assinatura** guia, selecione o **assinar o assembly** caixa de seleção.  
  
3.  No **escolher um arquivo de chave de nome forte** , escolha  **\<novo... >**.  
  
4.  No **criar chave de nome forte** caixa de diálogo, digite um nome, limpe o **proteger o arquivo de chaves com uma senha** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
5.  Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Para obter a chave pública token para o assembly do Assistente  
  
1.  Em uma janela de Prompt de comando do Visual Studio, execute o seguinte comando, substituindo *PathToWizardAssembly* com o caminho completo para o assembly ItemTemplateWizard.dll criado para o projeto ItemTemplateWizard em seu desenvolvimento computador.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     O token de chave pública para o assembly ItemTemplateWizard.dll é gravado para a janela de Prompt de comando do Visual Studio.  
  
2.  Mantenha a janela de Prompt de comando do Visual Studio aberta. Você precisará do token de chave pública para concluir o procedimento a seguir.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Para adicionar uma referência ao assembly do assistente no arquivo. vstemplate.  
  
1.  Em **Solution Explorer**, expanda o **ItemTemplate** nó do projeto e, em seguida, abra o arquivo ItemTemplate.vstemplate.  
  
2.  No final do arquivo, adicione o seguinte `WizardExtension` elemento entre o `</TemplateContent>` e `</VSTemplate>` marcas. Substitua o *YourToken* valor o `PublicKeyToken` atributo com o token de chave pública que você obteve no procedimento anterior.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Para obter mais informações sobre o `WizardExtension` elemento, consulte [elemento WizardExtension &#40; Modelos do Visual Studio &#41; ](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Salve e feche o arquivo.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Adicionando parâmetros substituíveis no arquivo Elements no modelo de Item  
 Adicione vários parâmetros substituíveis no arquivo Elements no projeto ItemTemplate. Esses parâmetros são inicializados no `PopulateReplacementDictionary` método o `CustomActionWizard` classe definido anteriormente. Quando um usuário adiciona um item de projeto de ação personalizada para um projeto, o Visual Studio substitui automaticamente esses parâmetros no arquivo Elements no novo item de projeto com os valores que elas especificadas no assistente.  
  
 Um parâmetro de substituição é um token que inicia e termina com o caractere de cifrão ($). Além de definir seus próprios parâmetros substituíveis, você pode usar os parâmetros internos que o sistema de projeto do SharePoint define e inicializa. Para obter mais informações, consulte [parâmetros substituíveis](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Para adicionar parâmetros substituíveis ao arquivo Elements.  
  
1.  No projeto ItemTemplate, substitua o conteúdo do arquivo Elements XML a seguir.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     O novo XML altera os valores da `Id`, `GroupId`, `Location`, `Description`, e `Url` atributos para os parâmetros substituíveis.  
  
2.  Salve e feche o arquivo.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Adicionando o assistente ao pacote VSIX  
 No arquivo source.extension.vsixmanifest no projeto VSIX, adicione uma referência ao projeto do Assistente para que ele é implantado com o pacote do VSIX que contém o item de projeto.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Para adicionar o Assistente para o pacote VSIX  
  
1.  Em **Gerenciador de soluções**, abra o menu de atalho do **source.extension.vsixmanifest** arquivo no projeto CustomActionProjectItem e, em seguida, escolha **abrir** abrir o arquivo no editor de manifesto.  
  
2.  No editor de manifesto, escolha o **ativos** guia e, em seguida, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
3.  No **tipo** , escolha **Microsoft.VisualStudio.Assembly**.  
  
4.  No **fonte** , escolha **um projeto na solução atual**.  
  
5.  No **projeto** , escolha **ItemTemplateWizard**e, em seguida, escolha o **Okey** botão.  
  
6.  Na barra de menus, escolha **criar**, **compilar solução**e, em seguida, certifique-se de que a solução compilado sem erros.  
  
## <a name="testing-the-wizard"></a>O Assistente de teste  
 Agora você está pronto para testar o assistente. Primeiro, inicie a depuração a solução CustomActionProjectItem na instância experimental do Visual Studio. Em seguida, teste o Assistente para o item de projeto de ação personalizada em um projeto do SharePoint na instância experimental do Visual Studio. Por fim, compilar e executar o projeto do SharePoint para verificar se a ação personalizada funciona conforme o esperado.  
  
#### <a name="to-start-to-debug-the-solution"></a>Para iniciar a depuração da solução  
  
1.  Reinicie o Visual Studio com credenciais administrativas e, em seguida, abra a solução de CustomActionProjectItem.  
  
2.  No projeto ItemTemplateWizard, abra o arquivo de código CustomActionWizard e, em seguida, adicione um ponto de interrupção para a primeira linha do código no `RunStarted` método.  
  
3.  Na barra de menus, escolha **depurar**, **exceções**.  
  
4.  No **exceções** caixa de diálogo caixa, certifique-se de que o **Thrown** e **manipulado pelo usuário** caixas de seleção para **Common Language Runtime Exceptions**serão eliminadas e, em seguida, escolha o **Okey** botão.  
  
5.  Iniciar a depuração, escolhendo a tecla F5 ou, na barra de menus, escolhendo **depurar**, **iniciar depuração**.  
  
     Visual Studio instala a extensão para %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 de projeto de ação e inicia uma instância experimental do Visual Studio. Você testará o item de projeto nesta instância do Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Para testar o assistente no Visual Studio  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
2.  Expanda o **Visual C#** ou **Visual Basic** nó (dependendo da linguagem que dá suporte a seu modelo de item), expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
3.  Na lista de modelos de projeto, escolha **projeto do SharePoint 2010**, nomeie o projeto **CustomActionWizardTest**e, em seguida, escolha o **Okey** botão.  
  
4.  No **Assistente de personalização do SharePoint**, insira a URL do site que você deseja usar para depuração e, em seguida, escolha o **concluir** botão.  
  
5.  Em **Solution Explorer**, abra o menu de atalho para o nó do projeto, escolha **adicionar**e, em seguida, escolha **Novo Item**.  
  
6.  No **Adicionar Novo Item - CustomItemWizardTest** caixa de diálogo caixa, expanda o **SharePoint** nó e, em seguida, expanda o **2010** nó.  
  
7.  Na lista de itens de projeto, escolha o **ação personalizada** item e, em seguida, escolha o **adicionar** botão.  
  
8.  Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definiu anteriormente no `RunStarted` método.  
  
9. Continuar a depuração do projeto, escolha a tecla F5 ou, na barra de menus, escolhendo **depurar**, **continuar**.  
  
     O Assistente de personalização do SharePoint é exibida.  
  
10. Em **local**, escolha o **Editar lista** botão de opção.  
  
11. No **ID do grupo** , escolha **comunicações**.  
  
12. No **título** , digite **SharePoint Developer Center**.  
  
13. No **descrição** , digite **abre o site do SharePoint Developer Center**.  
  
14. No **URL** , digite **http://msdn.microsoft.com/sharepoint/default.aspx**e, em seguida, escolha o **concluir** botão.  
  
     o Visual Studio adiciona um item chamado **CustomAction1** no seu projeto e abre o Elements arquivo no editor. Verifique se Elements contém os valores que você especificou no assistente.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Para testar a ação personalizada no SharePoint  
  
1.  Na instância experimental do Visual Studio, pressione a tecla F5 ou, na barra de menus, escolha **depurar**, **iniciar depuração**.  
  
     A ação personalizada é embalada e implantada no site do SharePoint especificado pelo **URL do Site** propriedade do projeto e o navegador da web abre a página padrão deste site.  
  
    > [!NOTE]  
    >  Se o **desabilitado de depuração de Script** caixa de diálogo for exibida, escolha o **Sim** botão.  
  
2.  Na área de listas do site do SharePoint, escolha o **tarefas** link.  
  
     O **tarefas - todas as tarefas** página será exibida.  
  
3.  No **lista ferramentas** guia da faixa de opções, escolha o **lista** guia e, em seguida, no **configurações** grupo, escolha **as configurações da lista**.  
  
     O **as configurações da lista** página será exibida.  
  
4.  Sob o **comunicações** título na parte superior da página, escolha o **SharePoint Developer Center** vincular, verifique se o navegador abre o site http://msdn.microsoft.com/sharepoint/ default. aspx e, em seguida, feche o navegador.  
  
## <a name="cleaning-up-the-development-computer"></a>Limpando o computador de desenvolvimento  
 Depois de concluir o teste de item de projeto, remova o modelo de item de projeto da instância experimental do Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Para limpar o computador de desenvolvimento  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
     A caixa de diálogo **Extensões e Atualizações** é aberta.  
  
2.  Na lista de extensões, escolha o **Item de projeto de ação personalizado** extensão e, em seguida, escolha o **desinstalação** botão.  
  
3.  Na caixa de diálogo que aparece, escolha o **Sim** botão para confirmar que você deseja desinstalar a extensão e, em seguida, escolha o **reiniciar agora** botão para concluir a desinstalação.  
  
4.  Feche ambas as instâncias do Visual Studio (a instância experimental e a instância do Visual Studio, em que a solução CustomActionProjectItem estiver aberta).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Definindo tipos de Item de projeto do SharePoint personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Criando modelos de projeto e modelos de Item para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Referência de esquema de modelo do Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Como: usar assistentes com modelos de projeto](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [IDs e locais de ação personalizada padrão](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  