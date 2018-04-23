---
title: Criando páginas de aplicativo do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68731e2a0c933f3f48f3a2211a9d17ca21e50242
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-application-pages-for-sharepoint"></a>Criando páginas de aplicativo do SharePoint
  Um *página de aplicativo* é uma página da Web do ASP.NET que é projetada para uso em um site do SharePoint. Páginas de aplicativo são um tipo especializado de página ASP.NET. A principal diferença entre uma página de aplicativo e uma página ASP.NET padrão é que uma página de aplicativo contém conteúdo que é mesclado com uma página mestre do SharePoint. Uma página mestra permite que as páginas de aplicativos que compartilham a mesma aparência e comportamento como outras páginas em um site.  
  
 O Visual Studio permite que você crie páginas de aplicativo usando um designer. O designer exibe uma área de conteúdo para cada espaço reservado para conteúdo que é definido em uma página mestra. Você pode criar a página de aplicativo arrastando controles a essas áreas de conteúdo.  
  
## <a name="application-pages"></a>Páginas de aplicativo  
 Páginas de aplicativo são compartilhadas entre todos os sites no servidor, enquanto uma página do site é um site específica. Para obter mais informações, [tipos de página do SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
 Por padrão, a maioria das páginas que aparecem quando você cria um site do SharePoint é páginas do site. Uma página de site pode ser adicionada a uma biblioteca de página do SharePoint. Os usuários podem personalizar uma página do site usando ferramentas como o SharePoint Designer. Uma página do site também pode hospedar recursos como dinâmico Web Parts e zonas de Web Part.  
  
 Páginas de aplicativo não podem executar estas ações. No entanto, uma página de aplicativo é o melhor tipo de página para criar a página para conter o código personalizado. Embora você possa adicionar código personalizado para uma página do site, o código para executar quando o usuário personaliza a página usando ferramentas como o SharePoint Designer.  
  
> [!NOTE]  
>  O Visual Studio não fornece modelos para ajudarão-lo a criam páginas de site para um site do SharePoint. Para obter mais informações, consulte [tipos de página do SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## <a name="creating-an-application-page"></a>Criando uma Página de Aplicativo  
 Para criar uma página de aplicativo, adicione um **página de aplicativo** item para um projeto do SharePoint. Quando você cria uma página de aplicativo, o Visual Studio adiciona as seguintes pastas ao seu projeto:  
  
|Pasta|Descrição|  
|------------|-----------------|  
|Layouts|Mapeia para o diretório virtual layouts do sistema de arquivos do SharePoint.|  
|Subpasta layouts|Contém os arquivos que compõem a página de aplicativo. Por padrão, esta pasta tem o mesmo nome de seu projeto. Você pode renomear esta pasta a qualquer momento. Quando você executar o projeto, o Visual Studio implanta essa pasta para o diretório virtual layouts do sistema de arquivos do SharePoint.|  
  
 O Visual Studio adiciona os seguintes arquivos ao seu projeto:  
  
|Arquivo|Descrição|  
|----------|-----------------|  
|Arquivo de página do ASP.NET (. aspx)|Contém a marcação XML que define a página.|  
|Arquivo de código de página do aplicativo|Contém o código por trás da página do aplicativo. Adicione o código que trata os eventos nesse arquivo.|  
|Arquivo de código de designer de página do aplicativo|Contém o código que é gerado pelo designer. Não edite esse arquivo diretamente.|  
  
## <a name="designing-and-debugging-an-application-page"></a>Criando e depurando uma página de aplicativo  
 Crie o conteúdo de uma página de aplicativo usando o modo de exibição designer no Visual Studio. Esse designer é exibida quando você abre a página de aplicativo em seu projeto (clicando duas vezes nele ou abrindo o menu de atalho e, em seguida, escolhendo **abrir**) e, em seguida, escolha o **Design** botão na parte inferior o editor.  
  
> [!NOTE]  
>  Você pode criar a página somente no **fonte** visualização do designer. O **Design** visualização do designer está desabilitada para as páginas do aplicativo.  
  
 Você pode depurar uma página de aplicativo, assim como você faria para depurar outros itens de projeto do SharePoint no Visual Studio. Quando você inicia o depurador do Visual Studio, o Visual Studio abrirá o site do SharePoint.  
  
 Para exibir a página de aplicativo, você deve navegar manualmente para o local da página do aplicativo (por exemplo: http://*nome_do_servidor*/_layouts/*Project_Name*/ApplicationPage1.aspx).  
  
 Para obter mais informações sobre como depurar projetos do SharePoint, consulte [Solucionando problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="choosing-a-master-page"></a>Escolhendo uma página mestra  
 Por padrão, um **página de aplicativo** item faz referência à página mestre do site que você está usando para depurar seu projeto. Que página é chamada v4.master e você pode encontrar listadas no **Galeria de páginas mestras** do site do SharePoint.  
  
 Você pode alterar explicitamente a página mestra é usada pela página de aplicativo, definindo o `MasterPageFile` atributo do aplicativo `Page` elemento. (Por exemplo: `MasterPageFile="~/_layouts/applicationv4.master"`). Na verdade, você deve definir esse atributo se páginas mestras dinâmicas não estiverem habilitadas no servidor do SharePoint. Para obter mais informações sobre páginas mestras no SharePoint, consulte [páginas mestras](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvimento do SharePoint Foundation em camadas](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Visão geral do ASP.NET](/aspnet/overview)   
 [Páginas da Web do ASP.NET](/aspnet/web-pages/index)   
  
  