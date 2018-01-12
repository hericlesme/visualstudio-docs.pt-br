---
title: 'Como: adicionar uma entidade para um modelo | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2ef3885f2a290fd1d4193daf9436a08ae5588a0d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-an-entity-to-a-model"></a>Como adicionar uma entidade a um modelo
  Para criar uma entidade, adicione um controle de entidade do Visual Studio **caixa de ferramentas** para o designer de conectividade de dados de negócios (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Para adicionar uma entidade no modelo  
  
1.  Criar um projeto BDC ou abrir um projeto BDC existente. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  No **caixa de ferramentas**, do **BusinessDataCatalog** de grupo, adicione um **entidade** controle no designer.  
  
     A nova entidade é exibida no designer. O Visual Studio adiciona um `<Entity>` elemento para o XML do arquivo de modelo BDC em seu projeto. Para obter mais informações sobre os atributos de um elemento de entidade, consulte [entidade](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  No designer, abra o menu de atalho para a entidade, escolha **adicionar**e, em seguida, escolha **identificador**.  
  
     Um novo identificador aparece na entidade.  
  
    > [!NOTE]  
    >  Você pode alterar o nome da entidade e o identificador de **propriedades** janela.  
  
4.  Defina os campos da entidade em uma classe. Você pode adicionar uma nova classe ao projeto ou usar uma classe existente criada usando outras ferramentas, como o Object Relational Designer (O/R Designer). O exemplo a seguir mostra uma classe de entidade nomeada contato.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Como: adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Como: adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Como: adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Como adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  