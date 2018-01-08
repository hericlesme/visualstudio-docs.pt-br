---
title: 'Como: criar um modelo BDC | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fb9cab573243882fb0bd410d69941b01ae290994
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-bdc-model"></a>Como criar um modelo BDC
  Você pode criar um modelo de conectividade de dados de negócios (BDC) usando o modelo para esse tipo de item e, em seguida, adicionando o modelo a qualquer projeto do SharePoint. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md). Para obter mais informações sobre como criar o modelo, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Para criar um projeto BDC  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
    > [!NOTE]  
    >  Se seu IDE está definido para usar configurações de desenvolvimento do Visual Basic, escolha **arquivo**, **novo projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
2.  Em um **Visual Basic** ou **Visual C#**, escolha **Office/SharePoint**, **soluções do SharePoint**.  
  
3.  No **modelos** painel, escolha o **SharePoint 2013 - projeto vazio** item e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é aberto.  
  
4.  No **especificar o nível de site e segurança de depuração** página, especifique a URL de um site do SharePoint no computador local, escolha o **implantar como solução de farm** botão de opção e, em seguida, escolha o **Concluir** botão.  
  
     Você testará o modelo no site do SharePoint que você especificou.  
  
    > [!IMPORTANT]  
    >  Você deve implantar o projeto como uma solução de farm porque BDC modelos dão suporte a soluções do farm.  
  
     Um projeto vazio do SharePoint é criado.  
  
5.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
6.  No **Adicionar Novo Item** caixa de diálogo caixa, escolha o **Office/SharePoint** nó.  
  
7.  Na lista de modelos do SharePoint, escolha **modelo de conectividade de dados corporativos (solução de Farm somente)**.  
  
8.  No **nome** caixa, especifique um nome para o modelo BDC e, em seguida, escolha o **adicionar** botão.  
  
     Um **modelo de conectividade de dados corporativos** item é adicionado ao projeto. Por padrão, o modelo é exibido no designer de BDC. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Como: adicionar um arquivo de modelo BDC existente a um projeto do SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Como: usar um arquivo de recurso para especificar nomes localizados, propriedades e permissões](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Como: incluir um Assembly personalizado em um recurso BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  