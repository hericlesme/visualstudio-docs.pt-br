---
title: "Passo a passo: Criando uma extensão de projeto do SharePoint | Microsoft Docs"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2ca99a5ad13989f29126b23a93055b174bb49150
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-sharepoint-project-extension"></a>Instruções passo a passo: criando uma extensão de projeto do SharePoint
  Este passo a passo ilustra como criar uma extensão para projetos do SharePoint. Você pode usar uma extensão de projeto para responder a eventos de nível de projeto, como quando um projeto é adicionado, excluído ou renomeado. Você também pode adicionar propriedades personalizadas ou responder quando uma alteração de valor de propriedade. Ao contrário das extensões de item de projeto, extensões de projeto não podem ser associadas um determinado tipo de projeto do SharePoint. Quando você cria uma extensão de projeto, a extensão carrega quando qualquer tipo de projeto do SharePoint é aberto em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Neste passo a passo, você criará uma propriedade booleana personalizada que é adicionada a qualquer projeto do SharePoint criado na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Quando definido como **True**, a nova propriedade adiciona ou mapas, uma pasta de recursos de imagens ao seu projeto. Quando definido como **False**, a pasta de imagens é removida, se ele existir. Para obter mais informações, consulte [como: adicionar e remover pastas mapeadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensão para projetos do SharePoint que faz o seguinte:  
  
    -   Adiciona uma propriedade de projeto personalizados para a janela de propriedades. A propriedade se aplica a qualquer projeto do SharePoint.  
  
    -   Usa o modelo de objeto do projeto do SharePoint para adicionar uma pasta mapeada para um projeto.  
  
    -   Usa o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (DTE) para excluir uma pasta mapeada do projeto de modelo de objeto de automação.  
  
-   Criando um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para implantar o assembly de extensão da propriedade de projeto.  
  
-   Depurando e testando a propriedade de projeto.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisará dos seguintes componentes no computador de desenvolvimento para concluir este passo a passo:  
  
-   Edições do [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   O [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Este passo a passo usa o **projeto VSIX** modelo o [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] para criar um pacote do VSIX para implantar a extensão de propriedade do projeto. Para obter mais informações, consulte [estendendo as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="creating-the-projects"></a>Criando os Projetos  
 Para concluir este passo a passo, você deve criar dois projetos:  
  
-   Um projeto do VSIX para criar o pacote do VSIX para implantar a extensão do projeto.  
  
-   Um projeto de biblioteca de classe que implementa a extensão de projeto.  
  
 Criando projetos para iniciar o passo a passo.  
  
#### <a name="to-create-the-vsix-project"></a>Para criar o projeto do VSIX  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
3.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha o **extensibilidade** nó.  
  
    > [!NOTE]  
    >  Este nó estará disponível somente se você instalar o SDK do Visual Studio. Para obter mais informações, consulte a seção pré-requisitos neste tópico.  
  
4.  Na parte superior da caixa de diálogo, escolha **.NET Framework 4.5** na lista de versões do .NET Framework e, em seguida, escolha o **projeto VSIX** modelo.  
  
5.  No **nome** , digite **ProjectExtensionPackage**e, em seguida, escolha o **Okey** botão.  
  
     O **ProjectExtensionPackage** projeto aparece na **Gerenciador de soluções**.  
  
#### <a name="to-create-the-extension-project"></a>Para criar o projeto de extensão  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução, escolha **adicionar**e, em seguida, escolha **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual C#** ou **Visual Basic** nós e, em seguida, escolha **Windows**.  
  
3.  Na parte superior da caixa de diálogo, escolha **.NET Framework 4.5** na lista de versões do .NET Framework e, em seguida, escolha o **biblioteca de classes** modelo de projeto.  
  
4.  No **nome** , digite **ProjectExtension**e, em seguida, escolha o **Okey** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Adiciona o **ProjectExtension** projeto à solução e abre o arquivo de código Class1 padrão.  
  
5.  Exclua o arquivo de código Class1 do projeto.  
  
## <a name="configuring-the-project"></a>Configurando o projeto  
 Antes de escrever código para criar a extensão de projeto, adicione arquivos de código e referências de assembly para o projeto de extensão.  
  
#### <a name="to-configure-the-project"></a>Configurar o projeto  
  
1.  Adicionar um arquivo de código que é chamado **CustomProperty** para o projeto de ProjectExtension.  
  
2.  Abra o menu de atalho para o **ProjectExtension** do projeto e, em seguida, escolha **adicionar referência**.  
  
3.  No **Gerenciador de referências - CustomProperty** caixa de diálogo caixa, escolha o **Framework** nó e, em seguida, selecione a caixa de seleção ao lado de assemblies System.ComponentModel.Composition e System.  
  
4.  Escolha o **extensões** nó, selecione a caixa de seleção ao lado de assemblies Microsoft.VisualStudio.SharePoint e EnvDTE e, em seguida, escolha o **Okey** botão.  
  
5.  Em **Gerenciador de soluções**, sob o **referências** pasta para o **ProjectExtension** do projeto, escolha **EnvDTE**.  
  
6.  No **propriedades** janela, altere o **Embed Interop Types** propriedade **False**.  
  
## <a name="defining-the-new-sharepoint-project-property"></a>Definir a nova propriedade de projeto do SharePoint  
 Crie uma classe que define a extensão de projeto e o comportamento da nova propriedade de projeto. Para definir a nova extensão de projeto, a classe implementa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Implemente esta interface sempre que você deseja definir uma extensão para um projeto do SharePoint. Além disso, adicionar o <xref:System.ComponentModel.Composition.ExportAttribute> à classe. Este atributo permite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para descobrir e carregar sua <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementação. Passar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo para construtor o atributo do.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Para definir a nova propriedade de projeto do SharePoint  
  
1.  Cole o código a seguir no arquivo de código de CustomProperty.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="building-the-solution"></a>Compilar a solução  
 Em seguida, compile a solução para certificar-se de que ele foi compilado sem erros.  
  
#### <a name="to-build-the-solution"></a>Para compilar a solução  
  
1.  Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-property-extension"></a>Criando um pacote do VSIX para implantar a extensão de propriedade do projeto  
 Para implantar a extensão do projeto, use o projeto do VSIX em sua solução para criar um pacote do VSIX. Primeiro, configure o pacote VSIX, modificando o arquivo source.extension.vsixmanifest que está incluído no projeto do VSIX. Em seguida, crie o pacote do VSIX por compilar a solução.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Para configurar e criar o pacote VSIX  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o arquivo source.extension.vsixmanifest e, em seguida, escolha o **abrir** botão.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Abre o arquivo no designer de manifesto. As informações que aparecem no **metadados** guia também aparece no **extensões e atualizações**. Todos os pacotes do VSIX requerem o arquivo extension.vsixmanifest. Para obter mais informações sobre esse arquivo, consulte [1.0 referência do esquema de extensão de VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  No **nome do produto** , digite **personalizado projeto propriedade**.  
  
3.  No **autor** , digite **Contoso**.  
  
4.  No **descrição** , digite **uma propriedade personalizada de projeto do SharePoint que alterna o mapeamento da pasta de recursos de imagens ao projeto**.  
  
5.  Escolha o **ativos** guia e, em seguida, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
6.  No **tipo** , escolha **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Esse valor corresponde do `MEFComponent` elemento no arquivo extension.vsixmanifest. Este elemento Especifica o nome de um assembly de extensão do pacote VSIX. Para obter mais informações, consulte [MEFComponent Element (esquema de VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  No **fonte** , escolha o **um projeto na solução atual** botão de opção.  
  
8.  No **projeto** , escolha **ProjectExtension**.  
  
     Esse valor identifica o nome do assembly que você está criando no projeto.  
  
9. Escolha **Okey** para fechar o **adicionar novo ativo** caixa de diálogo.  
  
10. Na barra de menus, escolha **arquivo**, **Salvar tudo** quando você concluir e, em seguida, feche o designer de manifesto.  
  
11. Na barra de menus, escolha **criar**, **compilar solução**e, em seguida, certifique-se de que o projeto é compilado sem erros.  
  
12. Em **Solution Explorer**, abra o menu de atalho para o **ProjectExtensionPackage** do projeto e escolha o **Abrir pasta no Explorador de arquivos** botão.  
  
13. Em **Explorador de arquivos**, abra a pasta de saída de compilação do projeto ProjectExtensionPackage e, em seguida, verifique se a pasta contém um arquivo chamado ProjectExtensionPackage.vsix.  
  
     Por padrão, a pasta de saída de compilação é o. pasta \bin\debug sob a pasta que contém o arquivo de projeto.  
  
## <a name="testing-the-project-property"></a>A propriedade do projeto de teste  
 Agora você está pronto para testar a propriedade de projeto personalizados. É mais fácil depurar e testar a nova extensão de propriedade do projeto em uma instância experimental do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Esta instância do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] é criado quando você executa um VSIX ou outro projeto de extensibilidade. Depois de depurar o projeto, você pode instalar a extensão no seu sistema e, em seguida, continuar a depuração e teste-o em uma instância regular da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Para depurar e testar a extensão em uma instância experimental do Visual Studio  
  
1.  Reiniciar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] com credenciais administrativas e, em seguida, abra a solução ProjectExtensionPackage.  
  
2.  Iniciar uma compilação de depuração do projeto, escolha o **F5** chave ou, na barra de menus, escolhendo **depurar**, **iniciar depuração**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]instala a extensão %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1.0 de projeto e inicia uma instância experimental do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  Na instância experimental do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], crie um projeto do SharePoint para uma solução de farm e usar os valores padrão para os outros valores no assistente.  
  
    1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
    2.  Na parte superior do **novo projeto** caixa de diálogo caixa, escolha **.NET Framework 3.5** na lista de versões do .NET Framework.  
  
         Extensões de ferramentas do SharePoint exigem recursos nesta versão do [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  Sob o **modelos** nó, expanda o **Visual C#** ou **Visual Basic** nó, escolha o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
    4.  Escolha o **projeto do SharePoint 2010** modelo e, em seguida, digite **ModuleTest** como o nome do seu projeto.  
  
4.  Em **Solution Explorer**, escolha o **ModuleTest** nó do projeto.  
  
     Uma nova propriedade personalizada **pasta de imagens de mapa** aparece no **propriedades** janela com um valor padrão de **False**.  
  
5.  Altere o valor da propriedade **True**.  
  
     Uma pasta de recursos de imagens é adicionada ao projeto do SharePoint.  
  
6.  Altere o valor da propriedade de volta para **False**.  
  
     Se você escolher o **Sim** no botão de **excluir a pasta imagens?** caixa de diálogo, as imagens de pasta do recurso é excluída do projeto do SharePoint.  
  
7.  Feche a instância experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo projetos SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Como: adicionar uma propriedade a projetos do SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converter entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associando dados personalizados a extensões de Ferramentas do SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  