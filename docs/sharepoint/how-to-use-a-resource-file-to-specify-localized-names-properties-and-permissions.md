---
title: "Como: usar um arquivo de recurso para especificar nomes localizados, propriedades e permissões | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a8b61477ae3b588b2aeadf1c9d99618151825f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Como usar um arquivo de recurso para especificar nomes localizados, propriedades e permissões
  Usando um arquivo de recursos, fornecer nomes localizados, definir propriedades e aplicar permissões tor objetos que são definidos em um modelo de conectividade de dados de negócios (BDC). Para especificar essas informações, você adiciona um **recursos de conectividade de dados de negócios** item a um projeto que contém um **modelo de conectividade de dados corporativos** item. Em seguida, especifique nomes, propriedades e permissões editando o XML para o arquivo de recurso.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Para adicionar um arquivo de recurso BDC a um projeto do SharePoint  
  
1.  Em **Solution Explorer**, expanda a pasta do projeto do SharePoint e, em seguida, escolha a pasta que contém o modelo BDC.  
  
2.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
3.  Expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  No **Adicionar Novo Item** caixa de diálogo caixa, escolha **Item de recurso de conectividade de dados corporativos**.  
  
5.  No **nome** caixa, especifique o nome do arquivo de recurso e, em seguida, escolha o **adicionar** botão.  
  
     Um arquivo de recurso que tem a extensão de .bdcr é adicionado ao projeto e aberto para edição.  
  
6.  Adicione o XML para definir nomes localizados, propriedades e permissões que você deseja aplicar o modelo BDC.  
  
     Para obter informações sobre como definir esses elementos, consulte [modelo e arquivos de recurso](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar um arquivo de modelo BDC existente a um projeto do SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Como: criar um modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Como: incluir um Assembly personalizado em um recurso BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  