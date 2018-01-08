---
title: "Como: adicionar um método Updater | Microsoft Docs"
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
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a03a4038418415889d5394111e0960f0edf01b22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-updater-method"></a>Como adicionar um método Updater
  Você pode habilitar os usuários atualizem dados comerciais em uma lista externa do SharePoint, criando uma *Updater* método. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Para criar um método Updater  
  
1.  No designer de BDC, escolha uma entidade.  
  
2.  Na barra de menus, escolha **exibição**, **outras janelas**, **detalhes de método BDC**.  
  
     Abre a janela de detalhes de método BDC. Para obter mais informações sobre esta janela, consulte [visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  No **adicionar um método** , escolha **Criar atualizador método**.  
  
     O Visual Studio adiciona os seguintes elementos ao modelo. Esses elementos aparecem na janela de detalhes de método BDC.  
  
    -   Um método chamado **atualização**.  
  
    -   Um parâmetro de entrada para o método.  
  
    -   Um descritor de tipo para o parâmetro. Por padrão, o Visual Studio usa o descritor de tipo de entidade que você definiu para o método Finder (por exemplo: contato).  
  
    -   Uma instância de método para o método.  
  
     Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Se o identificador do tipo de entidade representa um campo em uma tabela de banco de dados que é gerado automaticamente, configure o **campo pré-Updater** propriedade **True**.  
  
4.  Em **Solution Explorer**, abra o menu de atalho, o serviço do arquivo de código que foi gerado para a entidade e, em seguida, escolha **Exibir código**.  
  
     O arquivo de código de serviço da entidade é aberto no Editor de códigos. Para obter mais informações sobre esse arquivo, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Adicione código para o método de atualização para atualizar dados. O exemplo a seguir atualiza as informações de um contato do banco de dados de exemplo AdventureWorks do SQL Server.  
  
    > [!NOTE]  
    >  Substitua o valor da `ServerName` campo com o nome do servidor.  
  
     [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Como: adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Como: adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Como: adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Como: adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Como: adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)  
  
  