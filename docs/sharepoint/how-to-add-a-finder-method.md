---
title: "Como: adicionar um método Finder | Microsoft Docs"
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
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b7594c650c1492b16e784ec649de6e66d1e6ec33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-finder-method"></a>Como adicionar um método Finder
  Para habilitar o serviço de conectividade de dados corporativos exibir uma lista de entidades em uma web part ou lista, você deve criar um *localizador* método. Um método Finder é um método que retorna uma coleção de instâncias de entidade. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Para criar um método Finder  
  
1.  No designer de BDC, escolha uma entidade.  
  
     Para obter mais informações, consulte [como: adicionar uma entidade para um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Na barra de menus, escolha **exibição**, **outras janelas**, **detalhes de método BDC**.  
  
     O **detalhes de método BDC** janela será aberta. Para obter mais informações sobre o **detalhes de método BDC** janela, consulte [visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  No **adicionar um método** , escolha **criar método do localizador**.  
  
     O Visual Studio adiciona um método, um parâmetro de retorno e um descritor de tipo.  
  
4.  Configure o descritor de tipo como um descritor de tipo de coleção de entidade. Para obter mais informações sobre como criar um descritor de tipo de coleção de entidade, consulte [como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Você não precisa executar essa etapa se você tiver adicionado um método Finder específico para a entidade. O Visual Studio usa o descritor de tipo definido no método Finder específico.  
  
5.  Em **Solution Explorer**, abra o menu de atalho, o serviço do arquivo de código que foi gerado para a entidade e, em seguida, escolha **Exibir código**. Para obter mais informações sobre o arquivo de código de serviço, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Adicione código para o método do localizador. Esse código executa as seguintes tarefas:  
  
    -   Recupera dados de uma fonte de dados.  
  
    -   Retorna uma lista de entidades para o serviço de catálogo de dados corporativos.  
  
     O exemplo a seguir retorna uma coleção de `Contact` entidades usando dados do banco de dados de exemplo AdventureWorks do SQL Server.  
  
    > [!NOTE]  
    >  Substitua o valor da `ServerName` campo com o nome do servidor.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Como: adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Como: adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Como: adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Como: adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)  
  
  