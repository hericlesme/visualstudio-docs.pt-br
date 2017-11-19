---
title: 'Passo a passo: Estendendo um tipo de Item de projeto do SharePoint | Microsoft Docs'
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8afe8ed1d59f8daec34a99b1479079a69a1bc740
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>Instruções passo a passo: estendendo um tipo de item do projeto do SharePoint
  Você pode usar o **modelo de conectividade de dados corporativos** item de projeto para criar um modelo para o serviço de conectividade de dados de negócios (BDC) no SharePoint. Por padrão, quando você cria um modelo usando o item de projeto, os dados no modelo não são exibidos aos usuários. Você também deve criar uma lista externa no SharePoint para permitir que os usuários exibir os dados.  
  
 Neste passo a passo, você criará uma extensão para o **modelo de conectividade de dados corporativos** item de projeto. Os desenvolvedores podem usar a extensão para criar uma lista externa em seu projeto que exibe os dados no modelo BDC. Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando uma extensão do Visual Studio que executa duas tarefas principais:  
  
    -   Ele gera uma lista externa que exibe os dados em um modelo BDC. A extensão usa o modelo de objeto para o sistema de projeto do SharePoint para gerar um arquivo Elements. XML que define a lista. Ele também adiciona o arquivo ao projeto para que ele é implantado junto com o modelo BDC.  
  
    -   Ele adiciona um item de menu de atalho para o **modelo de conectividade de dados corporativos** itens de projeto do **Gerenciador de soluções**. Os desenvolvedores podem clique neste item de menu para gerar uma lista externa para o modelo BDC.  
  
-   Criar um pacote de extensão de Visual Studio (VSIX) para implantar o assembly de extensão.  
  
-   A extensão de teste.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisará dos seguintes componentes no computador de desenvolvimento para concluir este passo a passo:  
  
-   Edições com suporte do Microsoft Windows, SharePoint e do Visual Studio. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   O [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Este passo a passo usa o **projeto VSIX** modelo no SDK para criar um pacote do VSIX para implantar o item de projeto. Para obter mais informações, consulte [estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conhecimento sobre os conceitos a seguir é útil, mas não necessário para concluir o passo a passo:  
  
-   O serviço BDC no [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Para obter mais informações, consulte [BDC arquitetura](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   O esquema XML para modelos BDC. Para obter mais informações, consulte [infra-estrutura do modelo BDC](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
 Para concluir este passo a passo, você precisa criar dois projetos:  
  
-   Um projeto do VSIX para criar o pacote do VSIX para implantar a extensão de item de projeto.  
  
-   Um projeto de biblioteca de classe que implementa a extensão de item de projeto.  
  
 Criando projetos para iniciar o passo a passo.  
  
#### <a name="to-create-the-vsix-project"></a>Para criar o projeto do VSIX  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
3.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **extensibilidade** nó.  
  
    > [!NOTE]  
    >  O **extensibilidade** nó estará disponível somente se você instalar o SDK do Visual Studio. Para obter mais informações, consulte a seção pré-requisitos neste tópico.  
  
4.  Na lista na parte superior do **novo projeto** caixa de diálogo caixa, escolha **.NET Framework 4.5**.  
  
     Extensões de ferramentas do SharePoint exigem recursos nesta versão do .NET Framework.  
  
5.  Escolha o **projeto VSIX** modelo.  
  
6.  No **nome** , digite **GenerateExternalDataLists**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o **GenerateExternalDataLists** projeto **Gerenciador de soluções**.  
  
7.  Se o arquivo source.extension.vsixmanifest não abrir automaticamente, abra o menu de atalho do projeto GenerateExternalDataLists e, em seguida, escolha **abrir**  
  
8.  Verifique se o arquivo source.extension.vsixmanifest tem uma entrada não está em branco (Digite Contoso) para o campo Autor, salve o arquivo e, em seguida, fechá-lo.  
  
#### <a name="to-create-the-extension-project"></a>Para criar o projeto de extensão  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **GenerateExternalDataLists** nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  No **adicionar novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **Windows** nó.  
  
3.  Na lista na parte superior da caixa de diálogo, escolha **.NET Framework 4.5**.  
  
4.  Na lista de modelos de projeto, escolha **biblioteca de classes**.  
  
5.  No **nome** , digite **BdcProjectItemExtension**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o **BdcProjectItemExtension** projeto à solução e abre o arquivo de código Class1 padrão.  
  
6.  Exclua o arquivo de código Class1 do projeto.  
  
## <a name="configuring-the-extension-project"></a>Configurando o projeto de extensão  
 Antes de escrever código para criar a extensão de item de projeto, adicione arquivos de código e referências de assembly para o projeto de extensão.  
  
#### <a name="to-configure-the-project"></a>Configurar o projeto  
  
1.  No projeto BdcProjectItemExtension, adicione dois arquivos de código que têm os seguintes nomes:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Escolha o projeto BdcProjectItemExtension e, em seguida, na barra de menus, escolha **projeto**, **adicionar referência**.  
  
3.  Sob o **Assemblies** nó, escolha o **Framework** nó e selecione a caixa de seleção para cada um dos seguintes assemblies:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  Sob o **Assemblies** nó, escolha o **extensões** nó e, em seguida, selecione a caixa de seleção para o assembly a seguir:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Selecione o botão **OK**.  
  
## <a name="defining-the-project-item-extension"></a>Definir a extensão de Item de projeto  
 Criar uma classe que define a extensão para o **modelo de conectividade de dados corporativos** item de projeto. Para definir a extensão, a classe implementa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface. Implemente esta interface sempre que você deseja estender um tipo existente de item de projeto.  
  
#### <a name="to-define-the-project-item-extension"></a>Para definir a extensão de item de projeto  
  
1.  Cole o seguinte código para o arquivo de código ProjectItemExtension.  
  
    > [!NOTE]  
    >  Depois de adicionar esse código, o projeto terá alguns erros de compilação. Esses erros desaparecerá quando você adiciona o código em etapas posteriores.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>Criando as listas de dados externa  
 Adicionar uma definição parcial do `GenerateExternalDataListsExtension` classe que cria uma lista de dados externa para cada entidade no modelo BDC. Para criar a lista de dados externos, esse código primeiro lê os dados de entidade no modelo BDC analisando os dados XML no arquivo de modelo BDC. Em seguida, ele cria uma instância de lista que é baseada no modelo BDC e adiciona essa instância de lista para o projeto.  
  
#### <a name="to-create-the-external-data-lists"></a>Para criar as listas de dados externa  
  
1.  Cole o seguinte código para o arquivo de código GenerateExternalDataLists.  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Nesse ponto no passo a passo, todo o código para a extensão de item de projeto está agora no projeto. Compile a solução para certificar-se de que o projeto é compilado sem erros.  
  
#### <a name="to-build-the-solution"></a>Para compilar a solução  
  
1.  Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>Criando um pacote do VSIX para implantar a extensão de Item de projeto  
 Para implantar a extensão, use o projeto do VSIX em sua solução para criar um pacote do VSIX. Primeiro, configure o pacote VSIX, modificando o arquivo source.extension.vsixmanifest que está incluído no projeto do VSIX. Em seguida, crie o pacote do VSIX por compilar a solução.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Para configurar e criar o pacote VSIX  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o arquivo source.extension.vsixmanifest no projeto GenerateExternalDataLists e, em seguida, escolha **abrir**.  
  
     O Visual Studio abrirá o arquivo no editor de manifesto. O arquivo source.extension.vsixmanifest é que a base para o arquivo extension.vsixmanifest é necessária para todos os pacotes VSIX. Para obter mais informações sobre esse arquivo, consulte [1.0 referência do esquema de extensão de VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  No **nome do produto** , digite **gerador da lista de dados externa**.  
  
3.  No **autor** , digite **Contoso**.  
  
4.  No **descrição** , digite **uma extensão para itens de projeto de modelo de conectividade de dados corporativos que pode ser usado para gerar listas de dados externa**.  
  
5.  Sobre o **ativos** guia do editor, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
6.  No **tipo** , escolha **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Esse valor corresponde do `MefComponent` elemento no arquivo extension.vsixmanifest. Este elemento Especifica o nome de um assembly de extensão do pacote VSIX. Para obter mais informações, consulte [MEFComponent Element (esquema de VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  No **fonte** , escolha **um projeto na solução atual**.  
  
8.  No **projeto** , escolha **BdcProjectItemExtension**e, em seguida, escolha o **Okey** botão.  
  
9. Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
10. Certifique-se de que o projeto é compilado e criada sem erros.  
  
11. Certifique-se de que a pasta de saída de compilação do projeto GenerateExternalDataLists agora contém o arquivo GenerateExternalDataLists.vsix.  
  
     Por padrão, a pasta de saída de compilação é o. pasta \bin\debug sob a pasta que contém o arquivo de projeto.  
  
## <a name="testing-the-project-item-extension"></a>A extensão de Item de projeto de teste  
 Agora você está pronto para testar a extensão de item de projeto. Primeiro, inicie a depuração do projeto de extensão na instância experimental do Visual Studio. Em seguida, use a extensão na instância experimental do Visual Studio para gerar uma lista externa para um modelo BDC. Por fim, abra a lista externa no site do SharePoint para verificar se ele funciona conforme o esperado.  
  
#### <a name="to-start-debugging-the-extension"></a>Para iniciar a depuração de extensão  
  
1.  Se necessário, reinicie o Visual Studio com credenciais administrativas e, em seguida, abra a solução de GenerateExternalDataLists.  
  
2.  No projeto BdcProjectItemExtension, abra o arquivo de código ProjectItemExtension e, em seguida, adicionar um ponto de interrupção à linha de código a `Initialize` método.  
  
3.  Abra o arquivo de código GenerateExternalDataLists e, em seguida, adicione um ponto de interrupção para a primeira linha do código no `GenerateExternalDataLists_Execute` método.  
  
4.  Iniciar a depuração, escolhendo a tecla F5 ou, na barra de menus, escolhendo **depurar**, **iniciar depuração**.  
  
     Visual Studio instala a extensão para %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Generator\1.0 de lista de dados e inicia uma instância experimental do Visual Studio. Você testará o item de projeto nesta instância do Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Para testar a extensão  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **modelos** nó, expanda o **Visual C#** nó, expanda o **SharePoint** nó e, em seguida, Escolha **2010**.  
  
3.  Na lista na parte superior da caixa de diálogo, verifique se **.NET Framework 3.5** está selecionado. Projetos para [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exigem essa versão do .NET Framework.  
  
4.  Na lista de modelos de projeto, escolha **projeto do SharePoint 2010**.  
  
5.  No **nome** , digite **SharePointProjectTestBDC**e, em seguida, escolha o **Okey** botão.  
  
6.  No Assistente de personalização do SharePoint, insira a URL do site que você deseja usar para depuração, escolha **implantar como uma solução de farm**e, em seguida, escolha o **concluir**botão.  
  
7.  Abra o menu de atalho para o projeto SharePointProjectTestBDC, escolha **adicionar**e, em seguida, escolha **Novo Item**.  
  
8.  No **adicionar NewItem - SharePointProjectTestBDC** caixa de diálogo caixa, expanda o nó de idiomas instalados, expanda o **SharePoint** nó.  
  
9. Escolha o **2010** nó e, em seguida, escolha o **modelo de conectividade de dados corporativos (somente solução de Farm)** modelo.  
  
10. No **nome** , digite **TestBDCModel**e, em seguida, escolha o **adicionar** botão.  
  
11. Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definir no `Initialize` método do arquivo de código ProjectItemExtension.  
  
12. Na instância de parada do Visual Studio, escolha o **F5** chave, ou na barra de menus, escolha **depurar**, **continuar** para continuar a depuração do projeto.  
  
13. Na instância experimental do Visual Studio, escolha o **F5** chave ou, na barra de menus, escolha **depurar**, **iniciar depuração** para compilar, implantar e executar o  **TestBDCModel** projeto.  
  
     O navegador da web abre a página padrão do site do SharePoint que é especificado para depuração.  
  
14. Verifique o **lista** seção na área de início rápido ainda não contém uma lista com base no modelo BDC padrão no projeto. Primeiro, você deve criar uma lista de dados externos, usando a interface do usuário do SharePoint ou usando a extensão de item de projeto.  
  
15. Feche o navegador da web.  
  
16. Na instância do Visual Studio que abriu o projeto TestBDCModel, abra o menu de atalho para o **TestBDCModel** nó **Solution Explorer**e, em seguida, escolha **gerar dados externos Lista**.  
  
17. Verifique se que o código em outra instância do Visual Studio para no ponto de interrupção que você definir no `GenerateExternalDataLists_Execute` método. Escolha o **F5** chave ou, na barra de menus, escolha **depurar**, **continuar** para continuar a depuração do projeto.  
  
18. A instância experimental do Visual Studio adiciona uma instância de lista chamado **Entity1DataList** para o TestBDCModel projeto e a instância também gera um recurso chamado **Feature2** para obter a lista instância.  
  
19. Escolha o **F5** chave ou, na barra de menus, escolha **depurar**, **iniciar depuração** para compilar, implantar e executar o projeto TestBDCModel.  
  
     O navegador da web abre a página padrão do site do SharePoint que é usado para depuração.  
  
20. No **lista** seção da área de início rápido, escolha o **Entity1DataList** lista.  
  
21. Verifique se a lista contém colunas que são nomeadas Identifier1 e a mensagem, além de um item que tem um valor de Identifier1 de 0 e um valor de mensagem de Hello World.  
  
     O **modelo de conectividade de dados corporativos** modelo de projeto gera o modelo BDC padrão que fornece todos esses dados.  
  
22. Feche o navegador da web.  
  
## <a name="cleaning-up-the-development-computer"></a>Limpando o computador de desenvolvimento  
 Depois de concluir o teste a extensão de item de projeto, remova a lista externa e o modelo BDC do site do SharePoint e remover a extensão de item de projeto do Visual Studio.  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Para remover a lista de dados externos do site do SharePoint  
  
1.  Na área de início rápido do site do SharePoint, escolha o **Entity1DataList** lista.  
  
2.  Na faixa de opções no site do SharePoint, escolha o **lista** guia.  
  
3.  No **lista** guia o **configurações** de grupo, escolha **as configurações da lista**.  
  
4.  Em **permissões e gerenciamento**, escolha **excluir essa lista**e, em seguida, escolha **Okey** para confirmar que você deseja enviar a lista para a Lixeira.  
  
5.  Feche o navegador da web.  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Para remover o modelo BDC do site do SharePoint  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **criar**, **Retract**.  
  
     O Visual Studio remove o modelo BDC do site do SharePoint.  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Para remover a extensão de item de projeto do Visual Studio  
  
1.  Na instância experimental do Visual Studio, na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
     A caixa de diálogo **Extensões e Atualizações** é aberta.  
  
2.  Na lista de extensões, escolha **gerador da lista de dados externa**e, em seguida, escolha o **desinstalação** botão.  
  
3.  Na caixa de diálogo que aparece, escolha **Sim** para confirmar que você deseja desinstalar a extensão.  
  
4.  Escolha **reiniciar agora** para concluir a desinstalação.  
  
5.  Feche ambas as instâncias do Visual Studio (a instância experimental e a instância em que a solução GenerateExternalDataLists estiver aberta).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Designando um modelo de Conectividade de Dados Corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  