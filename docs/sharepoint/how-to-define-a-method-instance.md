---
title: 'Como: definir uma instância de método | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44a31af455b09db5fb359339cee8da7b3ca0c77e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-define-a-method-instance"></a>Como definir uma instância de método
  Você deve definir pelo menos uma instância de método para cada método em seu modelo.  
  
 Adicionar uma instância de método usando o **detalhes de método BDC** janela. Quando você adicionar a instância de método, o Visual Studio adiciona um `<MethodInstance>` elemento para o XML do arquivo de modelo em seu projeto. Para obter mais informações sobre os atributos de uma `<MethodInstance>` elemento, consulte [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Para definir uma instância de método  
  
1.  No **detalhes de método BDC** janela, expanda o nó de um método e, em seguida, expanda o **instâncias** nó.  
  
2.  No **adicionar uma instância de método** , escolha **criar instância do localizador**.  
  
     Uma nova instância de método aparece sob o **instâncias** nó.  
  
3.  Na barra de menus, escolha **exibição**, escolha **janela propriedades**.  
  
4.  No **propriedades** janela, defina as propriedades da instância do método. Para obter mais informações sobre cada propriedade, consulte [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Como: adicionar uma entidade em um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Designando um modelo de Conectividade de Dados Corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  