---
title: Criando uma associação entre entidades | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3d0475653fe3c5950e39e9f8293d5179e9380db6
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692165"
---
# <a name="creating-an-association-between-entities"></a>Criando uma associação entre entidades
  Você pode definir relações entre entidades em seu modelo de conectividade de dados de negócios (BDC) ao criar associações. O Visual Studio gera os métodos que fornecem os consumidores do modelo com informações sobre cada associação. Esses métodos podem ser consumidos pelo web parts do SharePoint, listas ou aplicativos personalizados para exibir relações de dados em uma interface de usuário (IU).  
  
## <a name="create-an-association"></a>Criar uma associação
 Crie uma associação escolhendo o **associação** controle no Visual Studio **caixa de ferramentas**, escolhendo a primeira entidade (chamada de entidade de origem) e, em seguida, a segunda entidade (chamado de entidade de destino). Você pode definir os detalhes da associação no **Editor de associação**. Para obter mais informações, consulte [como: criar uma associação entre entidades](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Métodos de associação
 Aplicativos como o web parts do SharePoint business dados consomem associações chamando métodos na classe de serviço de uma entidade. Você pode adicionar métodos à classe de serviço de uma entidade, selecionando-os no **Editor de associação**.  
  
 Por padrão, o **Editor de associação** adiciona um método de associação de navegação para as entidades de origem e de destino. Um método de navegação de associação da entidade de origem permite que os consumidores recuperar uma lista de entidades de destino. Um método de navegação de associação da entidade de destino permite que os consumidores recuperar a entidade de origem que está relacionada a uma entidade de destino.  
  
 Você deve adicionar o código para cada um desses métodos para retornar as informações apropriadas. Você também pode adicionar outros tipos de métodos para dar suporte a cenários mais avançados. Para obter mais informações sobre cada um desses métodos, consulte [suporte para operações](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Tipos de associações
 Você pode criar dois tipos de associações no designer de BDC: associações de baseada em chave estrangeiras e associações sem chave estrangeiras.  
  
### <a name="foreign-key-based-association"></a>Associação baseada em chave estrangeira
 Você pode criar uma associação de baseada em chave estrangeira, relacionando um identificador da entidade de origem para o tipo de descritores definidos na entidade de destino. Essa relação permite que os consumidores do modelo fornecer uma interface do usuário avançada para seus usuários. Por exemplo, um formulário do Outlook que permite que um usuário crie uma ordem de venda que pode exibir os clientes em uma lista suspensa; ou uma lista de pedidos de vendas no SharePoint que permite aos usuários abrir uma página de perfil para um cliente.  
  
 Para criar uma associação de baseada em chave estrangeira, relacionar identificadores e digite descritores que compartilham o mesmo nome e tipo. Por exemplo, você pode criar uma associação baseada em chave estrangeira entre uma `Contact` entidade e um `SalesOrder` entidade. O `SalesOrder` entidade retorna um `ContactID` descritor de tipo como parte do parâmetro de retorno dos métodos de localizador ou localizador específico. Ambos os descritores de tipo aparecem no **Editor de associação**. Para criar uma relação baseada em chave estrangeira entre a `Contact` entidade e `SalesOrder` entidade, escolha o `ContactID` identificador ao lado de cada um desses campos.  
  
 Adicione código para o método de navegador de associação da entidade de origem que retorna uma coleção de entidades de destino. O exemplo a seguir retorna as ordens de venda de um contato.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Adicione código para o método de navegador de associação da entidade de destino que retorna uma entidade de origem. O exemplo a seguir retorna o contato está relacionado à ordem de venda.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Associação sem chave estrangeira
 Você pode criar uma associação sem mapeando identificadores para descritores de tipo de campo. Crie esse tipo de associação quando a entidade de origem não tem uma relação direta com a entidade de destino. Por exemplo, um `SalesOrderDetail` tabela não tem uma chave estrangeira que mapeia para uma chave primária em um `Contact` tabela.  
  
 Se você deseja exibir informações de `SalesOrderDetail` tabela relacionada a um `Contact`, você pode criar uma associação sem chave estrangeira entre a `Contact` entidade e `SalesOrderDetail` entidade.  
  
 No método de navegação de associação a `Contact` entidade, retorno de `SalesOrderDetail` entidades unindo tabelas, ou chamando um procedimento armazenado.  
  
 O exemplo a seguir retorna os detalhes de todas as ordens de vendas unindo tabelas.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 No método de navegação de associação a `SalesOrderDetail` entidade, retornar relacionado `Contact`. O exemplo a seguir demonstra isso.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Consulte também
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Como: criar uma associação entre entidades](../sharepoint/how-to-create-an-association-between-entities.md)  
  
 