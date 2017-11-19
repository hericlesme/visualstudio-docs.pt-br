---
title: "Como: adicionar um descritor de filtro a um método Finder | Microsoft Docs"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 37aff0510af501b75aafe190fc412a0d4b9fd625
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Como adicionar um descritor de filtro a um método Finder
  Descritores de filtros permitem que os clientes do modelo passar valores para métodos antes de serem executados. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Um cenário comum é que desejam que os usuários do SharePoint recuperar instâncias de um tipo de conteúdo externo que correspondem a alguns critérios. Você pode dar suporte a esse cenário, adicionando um descritor de filtro para um método Finder.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Para adicionar um descritor de filtro a um método Finder  
  
1.  No **detalhes de método BDC** janela, expanda o nó de um método Finder, expanda o **parâmetros** nó e, em seguida, adicione um parâmetro de entrada. Para obter mais informações, consulte [como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  No **detalhes de método** janela, escolha o descritor do tipo do parâmetro.  
  
3.  Na barra de menus, escolha **exibição**, **janela propriedades**.  
  
4.  No **propriedades** janela, defina o **nome do tipo** propriedade para um tipo de dados que é apropriado para o filtro.  
  
     Por exemplo, um filtro pode usar a data do pedido para limitar o número de pedidos de vendas retornado pelo método. Para dar suporte ao filtro, o **nome do tipo** propriedade do descritor de tipo deve ser definida como **System. DateTime**.  
  
5.  No **detalhes de método** janela, expanda o **descritores de filtros** nó.  
  
6.  Em **adicionar um descritor de filtro** , escolha **criar descritor de filtro**.  
  
     Um novo descritor de filtro é exibido debaixo do **descritores de filtros** nó.  
  
7.  Na barra de menus, escolha **exibição**, **janela propriedades**.  
  
8.  No **propriedades** janela, escolha o **tipo** propriedade.  
  
9. Na lista que aparece para o **tipo** propriedade, escolha o padrão de filtragem que você deseja.  
  
     Por exemplo, para criar um filtro que usa uma data do pedido para limitar o número de pedidos de vendas retornado em um método Finder, escolha **comparação**. Um filtro de comparação garante que um método finder retorna apenas as instâncias que atendem a uma condição específica. Para obter mais informações sobre cada padrão de filtragem, consulte [tipos de filtros com suporte pelo BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. No **propriedades** janela, escolha o **descritores de tipo associada** propriedade.  
  
11. Na lista que aparece para o **descritores de tipo associada** propriedade, escolha o descritor do tipo que você criou anteriormente neste procedimento. O filtro está relacionado com o parâmetro de entrada do método do localizador.  
  
12. Adicione código ao método Finder que retorna dados. Você pode usar o parâmetro de entrada como uma condição em uma consulta select.  
  
     O exemplo a seguir retorna as ordens de venda com a data da ordem especificada.  
  
    > [!NOTE]  
    >  Substitua o valor da `ServerName` campo com o nome do servidor.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Como: adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  