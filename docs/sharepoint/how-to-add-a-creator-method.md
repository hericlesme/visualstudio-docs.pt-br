---
title: 'Como: adicionar um método Creator | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0424c6561b063b17f384215021a1300122dcbb1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-creator-method"></a>Como adicionar um método Creator
  Um método Creator adiciona novos dados à fonte de dados de uma entidade. O serviço de conectividade de dados de negócios (BDC) chama este método quando os usuários escolhem o **Novo Item** botão na faixa de opções de uma lista com base no modelo. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Para adicionar um método Creator  
  
1.  No designer de BDC, escolha uma entidade.  
  
2.  Na barra de menus, escolha **exibição**, **outras janelas**, **detalhes de método BDC**.  
  
     O **detalhes de método BDC** janela será aberta. Para obter mais informações sobre essa janela, consulte [visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  No **adicionar um método** , escolha **criar criador método**.  
  
     O Visual Studio adiciona os seguintes elementos ao modelo, e esses elementos aparecem no **detalhes de método BDC** janela.  
  
    -   Um método chamado **criar**.  
  
    -   Um parâmetro de entrada para o método.  
  
    -   Um parâmetro de retorno do método.  
  
    -   Descritores para os parâmetros de tipo.  
  
    -   Uma instância de método para o método.  
  
     Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Em **Solution Explorer**, abra o menu de atalho, o serviço do arquivo de código que foi gerado para a entidade e, em seguida, escolha **Exibir código**.  
  
     O arquivo de código de serviço da entidade é aberto no Editor de códigos. Para obter mais informações sobre o arquivo de código de serviço de entidade, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Adicione código ao método criador que adiciona dados à fonte de dados. O exemplo a seguir adiciona um contato ao banco de dados de exemplo AdventureWorks do SQL Server.  
  
    > [!NOTE]  
    >  Substitua o valor da `ServerName` campo com o nome do servidor.  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Como: adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Como: adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Como: adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Como: adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)  
  
  