---
title: "Como: adicionar um método Finder específico | Microsoft Docs"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6a5dbff1d4a4c739ce8ecab0807e2d74c62f999e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-specific-finder-method"></a>Como adicionar um método Finder específico
  Você pode retornar uma instância de entidade única, criando uma *localizador específico* método. O serviço de conectividade de dados de negócios (BDC) executa o método Finder específico quando um usuário seleciona uma entidade em uma web part de dados de negócios ou lista externa. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Para criar um método Finder específico  
  
1.  No designer de BDC, escolha uma entidade.  
  
     Para obter informações sobre como adicionar uma entidade para o designer BDC no Visual Studio, consulte [como: adicionar uma entidade para um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Na barra de menus, escolha **exibição**, **outras janelas**, **detalhes de método BDC**.  
  
     O **detalhes de método BDC** janela será aberta. Para obter mais informações sobre essa janela, consulte [visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  No **adicionar um método** , escolha **criar o método Finder específico**.  
  
     O Visual Studio adiciona os seguintes elementos ao modelo. Esses elementos aparecem no **detalhes de método BDC** janela.  
  
    -   Um método.  
  
    -   Um parâmetro de entrada para o método.  
  
    -   Um parâmetro de retorno do método.  
  
    -   Um descritor de tipo para cada parâmetro.  
  
    -   Uma instância de método para o método.  
  
     Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Abra o Visual Studio **propriedades** janela.  
  
5.  Configure o descritor de tipo de parâmetro de retorno como um descritor de tipo de entidade. Para obter informações sobre como criar um descritor de tipo de entidade, consulte [como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Você não precisa executar essa etapa se você tiver adicionado um método Finder à entidade. O Visual Studio usa o descritor do tipo que você definiu no método do localizador.  
  
    > [!NOTE]  
    >  Se o campo de identificador do tipo de entidade representa um campo em uma tabela de banco de dados que é gerada automaticamente, configure o **somente leitura** propriedade do campo de identificador para **True**.  
  
6.  No **detalhes de método** janela, escolha a instância de método do método.  
  
7.  No **janela propriedades**, defina o **retornar o nome do parâmetro** propriedade para o nome do parâmetro de retorno do método. Para obter mais informações sobre as propriedades de instância de método, consulte [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  Em **Solution Explorer**, abra o menu de atalho, o serviço do arquivo de código que foi gerado para a entidade e, em seguida, escolha **Exibir código**.  
  
     O arquivo de código de serviço da entidade é aberto no Editor de códigos. Para obter mais informações sobre o arquivo de código de serviço de entidade, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Adicione código ao método Finder específico. Esse código executa as seguintes tarefas:  
  
    -   Recupera um registro de uma fonte de dados.  
  
    -   Retorna uma entidade para o serviço de catálogo de dados corporativos.  
  
     O exemplo a seguir retorna um contato do banco de dados de exemplo AdventureWorks do SQL Server.  
  
    > [!NOTE]  
    >  Substitua o valor da `ServerName` campo com o nome do servidor.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Como: adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Como: adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Como: adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Como: adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)  
  
  