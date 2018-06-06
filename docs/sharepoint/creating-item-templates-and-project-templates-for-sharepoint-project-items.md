---
title: Criação de Item modelos e modelos de projeto para itens de projeto do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b789072b7a9cc84965e3d78a412631120783b40b
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765197"
---
# <a name="creating-item-templates-and-project-templates-for-sharepoint-project-items"></a>Criando modelos de projeto do SharePoint para itens de projeto e modelos de item
  Quando você define um tipo de item de projeto do SharePoint personalizado, você pode associá-lo com um modelo de item ou um modelo de projeto para que outros desenvolvedores podem usar o item de projeto no Visual Studio. Você também pode criar um Assistente para o modelo.  
  
 Por exemplo, o Visual Studio não inclui um modelo de projeto ou o modelo de item para adicionar um campo a um site do SharePoint. Você pode definir um tipo de item de projeto do SharePoint que representa um campo e, em seguida, criar um modelo de item que outros desenvolvedores podem usar para adicionar o item de campo para um projeto do SharePoint. Ou, você pode construir um modelo de projeto para que os desenvolvedores podem criar um novo projeto do SharePoint que contém o item de campo. Em ambos os casos, você também pode fornecer um assistente que é exibida quando os desenvolvedores usam o modelo. Este assistente pode coletar informações de desenvolvedores para configurar o novo item ou projeto.  
  
 Modelos de item e projeto são *. zip* arquivos que contêm arquivos que são usados pelo Visual Studio para criar um item de projeto ou o projeto. Para obter mais informações sobre os conceitos básicos de modelos de item e projeto, consulte [criando modelos de projeto e Item](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-item-templates"></a>Criar modelos de item
 Quando você cria um modelo de item para um item de projeto do SharePoint, há alguns arquivos que são sempre obrigatórias e arquivos opcionais que podem ser usados por determinados tipos de itens de projeto. Para uma explicação passo a passo que demonstra como definir um tipo de item de projeto do SharePoint e criar um modelo de item para ele, consulte [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 A tabela a seguir lista os arquivos necessários para criar um modelo de item para um item de projeto do SharePoint.  
  
|Arquivo necessário|Descrição|  
|-------------------|-----------------|  
|Um *. spdata* arquivo|Isso é um arquivo XML que especifica o conteúdo e o comportamento padrão do item de projeto. Esse arquivo deve ser incluído no modelo de item. Para obter mais informações sobre o conteúdo de *. spdata* arquivos, consulte [referência de esquema de Item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|Um *. vstemplate* arquivo.|Esse arquivo fornece o Visual Studio com as informações necessárias para exibir o modelo no **Adicionar Novo Item** caixa de diálogo e criar um item de projeto do modelo. Esse arquivo deve ser incluído no modelo de item. Para obter mais informações, consulte [arquivos de metadados de modelo do Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Um assembly de extensão do Visual Studio que implementa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface.|Este assembly define o comportamento de tempo de execução do item de projeto. Este assembly deve ser incluído no pacote do VSIX com o modelo de item. Para obter mais informações, consulte [definindo tipos de Item de projeto do SharePoint de personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md) e [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 A tabela a seguir lista alguns dos arquivos opcionais mais comuns que podem ser incluídos no modelo de item. Alguns tipos de itens de projeto podem exigir outros arquivos não listados aqui.  
  
|Arquivo opcional|Descrição|  
|-------------------|-----------------|  
|*Elements*|Um *elemento Feature* arquivo. Esse arquivo define a interface do usuário e o comportamento da personalização criado pelo item de projeto. Cada tipo de personalização, como instâncias de lista, tipos de conteúdo ou ações personalizadas, tem um esquema diferente que define o conteúdo desse arquivo. Para obter mais informações, consulte [blocos de construção: recursos](http://go.microsoft.com/fwlink/?LinkId=169183) e [esquemas de recurso](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|*Schema*|O arquivo de esquema para definições de lista. Para obter mais informações, consulte [blocos de construção: listas e bibliotecas de documentos](http://go.microsoft.com/fwlink/?LinkId=177792) e [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|*. WebPart*|Um *definição de Web Part* arquivo. Esse arquivo contém as configurações de propriedade de uma Web Part. Para obter mais informações, consulte [blocos de construção: Web Parts](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|*. ascx*|Um arquivo de controle de usuário ASP.NET. Esse arquivo define a interface do usuário de uma Web Part Visual.|  
|*. aspx*|Um arquivo de página do ASP.NET. Esse arquivo contém marcação XML que define uma página de aplicativo.|  
|*CS* ou *. vb* arquivos|Esses arquivos de código definem o comportamento das personalizações do SharePoint que têm um modelo de programação que pode ser acessado de Visual c# ou código do Visual Basic, como páginas de aplicativos, Web parts e fluxos de trabalho.|  
## <a name="create-project-templates"></a>Criar modelos de projeto
 Quando você cria um modelo de projeto do SharePoint, há alguns arquivos que estão sempre arquivos necessários e opcionais que podem ser usados por determinados tipos de projetos. Normalmente, os projetos do SharePoint incluem pelo menos um item de projeto do SharePoint. No entanto, isso não é necessário. Por exemplo, você pode definir um modelo de projeto do SharePoint que se destina a ser usado apenas para implantar soluções do SharePoint criadas em outros projetos.  
  
 Para uma explicação passo a passo que demonstra como definir um tipo de item de projeto do SharePoint e criar um modelo de projeto para ele, consulte [passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 A tabela a seguir lista os arquivos que devem ser incluídos em um modelo de projeto do SharePoint.  
  
|Arquivo necessário|Descrição|  
|-------------------|-----------------|  
|Um *. vstemplate* arquivo|Esse arquivo fornece o Visual Studio com as informações necessárias para exibir o modelo no **novo projeto** caixa de diálogo e criar um projeto do modelo. Para obter mais informações, consulte [arquivos de metadados de modelo do Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Um *. csproj* ou *. vbproj* arquivo|Este é o arquivo de projeto. Define o conteúdo e as configurações do projeto.|  
|*Pacote*|Esse arquivo define o pacote de implantação para o projeto. Quando você usar o Designer de pacote para personalizar o pacote de solução para o seu projeto, o Visual Studio armazena dados sobre o pacote de solução neste arquivo.<br /><br /> Quando você cria um modelo de projeto do SharePoint personalizado, é recomendável incluir apenas o conteúdo mínimo necessário no *pacote* arquivo e que você configure o pacote de solução por meio de APIs no <xref:Microsoft.VisualStudio.SharePoint.Packages> namespace em uma extensão que está associado com o modelo de projeto. Se você fizer isso, o modelo de projeto está protegido contra alterações futuras na estrutura do *pacote* arquivo. Para obter um exemplo que demonstra como criar um *pacote* com somente o mínimo necessário o conteúdo do arquivo, consulte [passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se você quiser modificar o *pacote* arquivo diretamente, você pode verificar o conteúdo usando o esquema em *% arquivos de programas (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd* .|  
|*Package.Template.xml*|Esse arquivo fornece a base para o arquivo de manifesto de solução (*manifest.xml*) para o pacote de solução do SharePoint (*. wsp*) que é gerada a partir do projeto. Você pode adicionar conteúdo a este arquivo se desejar especificar um comportamento que não se destina a ser alterado pelos usuários do seu tipo de projeto. Para obter mais informações, consulte [blocos de construção: soluções](http://go.microsoft.com/fwlink/?LinkId=169186) e [solução esquema](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Quando você cria um pacote de solução do projeto, o Visual Studio mescla o conteúdo do *pacote* e *Package.Template.xml* arquivo de manifesto de arquivos na solução. Para obter mais informações sobre a criação de pacotes de soluções, consulte [como: criar um pacote de solução do SharePoint (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 A tabela a seguir lista os arquivos opcionais que podem ser incluídos no modelo de projeto.  
  
|Arquivo opcional|Descrição|  
|-------------------|-----------------|  
|itens de projeto do SharePoint|Você pode incluir um ou mais arquivos. spdata que definem tipos de item de projeto do SharePoint. Cada *. spdata* arquivo deve ter uma correspondência <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementação em um assembly de extensão que é incluído no pacote do VSIX com o modelo de projeto. Para obter mais informações, consulte [criando modelos de Item](#creatingitemtemplates).<br /><br /> Normalmente, os projetos do SharePoint incluem pelo menos um item de projeto do SharePoint. No entanto, isso não é necessário.|  
|*{nome do recurso} .feature*|Esse arquivo define um recurso do SharePoint que é usado para agrupar vários itens de projeto para a implantação. Quando você usar o Designer de recursos para personalizar um recurso em seu projeto, o Visual Studio armazena dados sobre o recurso neste arquivo. Se você quiser agrupar os itens de projeto em recursos diferentes, você pode incluir vários *.feature* arquivos.<br /><br /> Quando você cria um modelo de projeto do SharePoint personalizado, é recomendável que você incluir o conteúdo mínimo necessário em cada *.feature* arquivo e que você configure recursos por meio de APIs no <xref:Microsoft.VisualStudio.SharePoint.Features> namespace em um extensão que está associado com o modelo de projeto. Se você fizer isso, o modelo de projeto está protegido contra alterações futuras na estrutura do *.feature* arquivo. Para obter um exemplo que demonstra como criar um *.feature* com somente o mínimo necessário o conteúdo do arquivo, consulte [passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se você deseja modificar uma *.feature* arquivo diretamente, você pode verificar o conteúdo usando o esquema em *% arquivos de programas (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*.|  
|*{nome do recurso). Template*|Esse arquivo fornece a base para o arquivo de manifesto do recurso (*Feature*) para cada recurso que é gerado a partir do projeto. Você pode adicionar conteúdo a este arquivo se desejar especificar um comportamento que não se destina a ser alterado pelos usuários do seu tipo de projeto. Para obter mais informações, consulte [blocos de construção: recursos](http://go.microsoft.com/fwlink/?LinkId=169183) e [Feature](http://go.microsoft.com/fwlink/?LinkId=177795) arquivos.<br /><br /> Quando você cria um pacote de solução do projeto, o Visual Studio mescla o conteúdo de cada par de *{featureName} .feature* arquivo e *{featureName}. Template* arquivos em um recurso de arquivo de manifesto. Para obter mais informações sobre a criação de pacotes de soluções, consulte [como: criar um pacote de solução do SharePoint (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## <a name="create-wizards-for-item-templates-and-project-templates"></a>Criar os assistentes para modelos de item e projeto
 Depois de definir um tipo de item de projeto do SharePoint e associá-lo a um modelo de item ou projeto, você também pode criar um assistente. O assistente exibe quando um desenvolvedor usa o modelo de item para adicionar o item de projeto do SharePoint a um projeto, ou quando um desenvolvedor usa o modelo de projeto para criar um novo projeto que contém o item de projeto do SharePoint. O assistente pode ser usado para coletar informações de desenvolvedores e inicializar o novo item de projeto do SharePoint.  
  
 Para instruções passo a passo que demonstre como criar assistentes para modelos de item e projeto, consulte [passo a passo: Criando um Item de projeto de ação personalizado com um modelo de Item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) e [passo a passo: Criando um Site Item de projeto de coluna com um modelo de projeto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Consulte também
 [Definindo tipos de Item de projeto do SharePoint personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Criando modelos de projeto e de item](/visualstudio/ide/creating-project-and-item-templates)  
  
 