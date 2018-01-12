---
title: 'Como: adicionar um arquivo de modelo BDC existente a um projeto do SharePoint | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f5f13377211a6b8a7a2035d85e1423be9d2bbb72
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Como adicionar um arquivo de modelo BDC existente a um projeto do SharePoint
  Você pode personalizar o pacote e reimplantar um modelo de conectividade de dados de negócios (BDC) usando o Visual Studio para adicionar o arquivo de modelo (.bdcm) a qualquer projeto de farm do SharePoint. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Para adicionar um arquivo de modelo BDC a um projeto do SharePoint  
  
1.  Em **Solution Explorer**, escolha a pasta para um projeto do SharePoint.  
  
2.  Na barra de menus, escolha **projeto**, **Add Existing Item**.  
  
3.  No **Add Existing Item** caixa de diálogo, navegue até o local do arquivo de definição de modelo que você deseja adicionar ao seu projeto, escolha o arquivo e, em seguida, escolha o **adicionar** botão.  
  
     Se o modelo não define uma *sistema de linha de negócios (LOB) do tipo .NET assembly*, o **assembly .NET adicionar LobSystem** caixa de diálogo é aberta.  
  
4.  Se a caixa de diálogo for exibida, execute uma das seguintes etapas:  
  
    -   Se você quiser escrever código personalizado e usar um designer para definir metadados para o modelo importado, escolha o **Sim** botão, o sistema de nome e, em seguida, escolha o **Okey** botão.  
  
    -   Caso contrário, escolha o **não** botão e, em seguida, escolha o **Okey** botão.  
  
     O **modelo de conectividade de dados corporativos** item é adicionado ao projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Como: criar um modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Como: usar um arquivo de recurso para especificar nomes localizados, propriedades e permissões](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Como: incluir um Assembly personalizado em um recurso BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  