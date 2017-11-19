---
title: "Criando páginas do SharePoint | Microsoft Docs"
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
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bef1fce26bbd9ea57073273f462ec484a46a647b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-pages-for-sharepoint"></a>Criando páginas para SharePoint
  Você pode criar páginas de aplicativo, páginas do site, páginas mestras e layouts de página para um site do SharePoint.  
  
 Você pode criar páginas de aplicativo usando um modelo no Visual Studio. Crie site páginas, páginas mestras e layouts de página, usando o SharePoint Designer. Em seguida, você pode importar essas páginas no Visual Studio para usá-los em um projeto do SharePoint.  
  
 Você também pode modificar a aparência e comportamento das páginas usando folhas de estilo em cascata, ECMAScript e temas.  
  
## <a name="types-of-sharepoint-pages"></a>Tipos de páginas do SharePoint  
 A tabela a seguir descreve os quatro tipos principais de páginas que contém um site do SharePoint.  
  
|Tipo de página|Descrição|  
|---------------|-----------------|  
|Páginas de aplicativo|Crie uma página de aplicativo, se você deseja que a página para conter o código personalizado ou se desejar que a página a serem compartilhados por vários sites. Caso contrário, uma página do site pode ser a melhor opção.|  
|Páginas do site|Crie uma página do site se você quiser executar qualquer uma das seguintes tarefas:<br /><br /> -Adicione a página a uma biblioteca do SharePoint.<br />-Habilite a página de recursos de host como dinâmico Web Parts e zonas de Web Part.<br />-Habilite usuários a personalizar a página usando o SharePoint Designer.<br /><br /> Não crie uma página do site se você deseja que a página para conter o código personalizado. Embora você possa adicionar código personalizado para uma página do site, o código para executar quando o usuário personaliza a página usando o SharePoint Designer.|  
|Páginas mestras|Crie uma página mestre, se você quiser definir uma estrutura comum para páginas do site e as páginas do aplicativo.|  
|Layouts de página|Layouts de página são específicos para [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] e permitem que você definir uma estrutura comum para páginas do site e as páginas do aplicativo.|  
  
 Para obter uma visão geral de cada tipo de página, consulte [blocos de construção: páginas e a Interface do usuário](http://go.microsoft.com/fwlink/?LinkID=182095), e [Layouts de página e páginas mestras](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="creating-application-pages"></a>Criando páginas de aplicativo  
 Você pode criar páginas de aplicativo no Visual Studio adicionando um **página de aplicativo** item para um projeto do SharePoint. Você pode adicionar controles para a página e, em seguida, manipular eventos de controle, adicionando o código.  
  
 Você pode definir pontos de interrupção no arquivo de código da página, inicie o depurador e testar a página em um site do SharePoint local sem executar etapas de configuração adicionais. Para obter mais informações, consulte [criando páginas de aplicativo para o SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>Criando Site páginas, páginas mestras e Layouts de página  
 Você pode criar layouts de página, páginas mestras e páginas do site usando o SharePoint Designer. Em seguida, você pode importar essas páginas no Visual Studio. Importe suas páginas se você quiser tirar proveito da implantação ou recursos de controle de origem que estão disponíveis no Visual Studio. Para obter mais informações, consulte [importar itens de um Site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Como é difícil modificar essas páginas após a importação, você deve criar essas páginas antes de importá-los.  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>Criando temas, ECMAScript e folhas de estilo em cascata  
 O Visual Studio não fornece modelos para desenvolver folhas de estilo em cascata (CSS), ECMAScript (JavaScript, JScript) ou arquivos de tema para sites do SharePoint. Você pode criar esses arquivos usando as orientações disponíveis no SDK do SharePoint ou usando ferramentas como o SharePoint Designer.  
  
 Você pode adicionar esses arquivos à sua solução, diretamente ou você pode importá-los. Em ambos os casos, você deve criar as pastas mapeadas apropriadas para cada item que você adicionar. Para obter mais informações sobre como criar uma pasta mapeada, consulte [como: adicionar e remover pastas mapeadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Para obter mais informações sobre a criação de folhas de estilo em cascata, consulte [em cascata uso classe de folhas de estilo no SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Para obter mais informações sobre como criar arquivos JavaScript e JScript para uma solução do SharePoint, consulte [configuração a um ASPX página básica para ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Para obter mais informações sobre os temas, consulte [blocos de construção: páginas e a Interface do usuário](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Criando páginas de aplicativo para o SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Descreve como adicionar a páginas de aplicativos:. aspx conteúdo que é mesclado com uma página mestre do SharePoint.|  
|[Como criar uma página de aplicativo](../sharepoint/how-to-create-an-application-page.md)|Mostra como criar páginas ASP.NET que são executados em um site do SharePoint.|  
|[Instruções passo a passo: criando uma página de aplicativo do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Mostra como criar e depurar uma página da Web do ASP.NET para um site do SharePoint.|  
  
  