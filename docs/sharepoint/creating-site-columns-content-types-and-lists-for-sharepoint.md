---
title: Criar colunas de Site, tipos de conteúdo e listas do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1025884bb23290c616a42a8cbbdcbad1d5814b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-site-columns-content-types-and-lists-for-sharepoint"></a>Criando colunas de site, tipos de conteúdo e listas para SharePoint
  Visual Studio fornece modelos de item de projeto para muitos diferentes fundamentais itens do SharePoint, incluindo *lista* e *tipos de conteúdo*, que podem incorporar as colunas de site (ou  *campos*). Os designers de novo para tipos de conteúdo e listas facilitam a criação desses itens mais fácil.  
  
## <a name="site-columns"></a>Colunas de site  
 Colunas de site são um dos elementos mais básicos, que você pode adicionar a um projeto do SharePoint. Uma coluna de site representa um tipo de dados, como um número de telefone, um comentário ou o nome da cidade de um contato em uma lista de contatos.  
  
 O novo modelo de item de projeto de coluna de site facilita criar colunas de site que na versão anterior do Visual Studio. Depois de criar uma nova coluna de site, você pode modificar o XML no arquivo de Elements da coluna de site para incluir as informações desejadas, como seu nome de exibição, seu tipo de dados e o grupo no qual você deseja que a coluna de site apareça no SharePoint. Para obter mais informações sobre colunas de site, consulte [Introdução às colunas](http://go.microsoft.com/fwlink/?LinkId=224996).  
  
## <a name="content-types-and-lists"></a>Listas e tipos de conteúdo  
 Listas e tipos de conteúdo estão entre com mais frequência elementos usados no SharePoint.  
  
 Um tipo de conteúdo define os metadados, o fluxo de trabalho e o comportamento de uma categoria de itens em uma biblioteca do SharePoint de lista ou documento. Por exemplo, você pode criar um tipo de conteúdo para obter informações em uma lista de contatos ou uma lista de tarefas. Um tipo de conteúdo de contato pode incluir colunas, como nome, Email, telefone e endereço. Um tipo de conteúdo que você define no nível do site é independente de qualquer lista ou biblioteca de documentos no site. Você pode usar o mesmo tipo de conteúdo com várias listas ou bibliotecas de documentos no site do SharePoint. Você também pode usar vários tipos de conteúdo na mesma lista ou biblioteca de documentos.  
  
 Uma lista é uma coleção de informações no SharePoint que você pode compartilhar com outras pessoas. Listas de conter linhas de colunas que contêm dados. Alguns exemplos de lista: uma lista de tarefas, uma lista de contatos e uma lista de avisos.  
  
 Os designers novo tipo de conteúdo e lista no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Verifique criando listas de tipos de conteúdo do site e muito mais fácil e mais intuitiva do que na versão anterior do Visual Studio. A interface do usuário permite que você construir visualmente listas e tipos de conteúdo de uma maneira familiar e permite classificar e agrupar dados em listas e usar títulos de grupo. Para obter mais informações sobre tipos de conteúdo, consulte [tipos de conteúdo](http://go.microsoft.com/fwlink/?LinkId=224997). Para obter mais informações sobre listas, consulte [lista formulários](http://go.microsoft.com/fwlink/?LinkId=224998) e [modos de exibição de lista](http://go.microsoft.com/fwlink/?LinkId=224999).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Instruções passo a passo: criar uma coluna de site, tipos de conteúdo e listas para o SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Demonstra como criar colunas de site que são usadas em um tipo de conteúdo personalizado. O tipo de conteúdo, em seguida, é usado em uma lista personalizada.|  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao desenvolvimento no SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  