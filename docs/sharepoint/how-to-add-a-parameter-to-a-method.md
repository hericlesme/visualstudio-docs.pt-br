---
title: "Como: adicionar um parâmetro a um método | Microsoft Docs"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f6810d69628c66a011123250b8e0efb8622f0be7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Como adicionar um parâmetro a um método
  Use um parâmetro para passar informações para o método ou para retornar informações de um método. Todos os métodos devem ter pelo menos um parâmetro. Para obter mais informações sobre como criar um parâmetro para dar suporte ao tipo do método que você deseja criar, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Quando você adicionar um parâmetro a um método, o Visual Studio adiciona o `<Parameter>` elemento para o XML do arquivo de modelo em seu projeto. Para obter mais informações sobre os atributos de uma `<Parameter>` elemento, consulte [parâmetro](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Para adicionar um parâmetro a um método  
  
1.  Adicione um método para uma entidade.  
  
2.  Na barra de menus, escolha **exibição**, **outras janelas**, **detalhes de método BDC**.  
  
     O **detalhes de método BDC** janela será aberta. Para obter mais informações, consulte [visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  No **detalhes de método BDC** janela, expanda o nó do método e, em seguida, expanda o **parâmetros** nó.  
  
4.  No **adicionar um parâmetro** , escolha **criar parâmetro**.  
  
     Um novo parâmetro aparece sob o **parâmetros** nó.  
  
5.  Na barra de menus, escolha **exibição**, **janela propriedades**.  
  
6.  No **propriedades** janela, defina o **nome** propriedade para qualquer nome que faça sentido. Por exemplo, se o método retornará os clientes, você pode nomear o método **GetCustomers**.  
  
7.  No **detalhes de método BDC** janela, abra a lista que é exibido para a direção do parâmetro e, em seguida, escolha **na**, **InOut**, **Out**, ou **retornar**.  
  
     Para obter mais informações sobre a direção de escolha do método de tipo que você está criando, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modificar o descritor de tipo do parâmetro. Para obter mais informações, consulte [como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Como: adicionar uma entidade em um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Como: definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)   
 [Designando um modelo de Conectividade de Dados Corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  