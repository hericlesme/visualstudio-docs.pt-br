---
title: 'Como: adicionar um parâmetro a um método | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9268fd0deb463a29c8e6d19e98ad63c86b965292
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767082"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Como: adicionar um parâmetro a um método
  Use um parâmetro para passar informações para o método ou para retornar informações de um método. Todos os métodos devem ter pelo menos um parâmetro. Para obter mais informações sobre como criar um parâmetro para dar suporte ao tipo do método que você deseja criar, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Quando você adicionar um parâmetro a um método, o Visual Studio adiciona o elemento de parâmetro para o XML do arquivo de modelo em seu projeto. Para obter mais informações sobre os atributos de um elemento de parâmetro, consulte [parâmetro](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Para adicionar um parâmetro a um método  
  
1.  Adicione um método para uma entidade.  
  
2.  Na barra de menus, escolha **exibição** > **outras janelas** > **detalhes de método BDC**.  
  
     O **detalhes de método BDC** janela será aberta. Para obter mais informações, consulte [visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  No **detalhes de método BDC** janela, expanda o nó do método e, em seguida, expanda o **parâmetros** nó.  
  
4.  No **adicionar um parâmetro** , escolha **criar parâmetro**.  
  
     Um novo parâmetro aparece sob o **parâmetros** nó.  
  
5.  Na barra de menus, escolha **exibição** > **janela propriedades**.  
  
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
  
