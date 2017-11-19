---
title: "Visão geral das ferramentas de Design de modelo BDC | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eaf6871f7ad9316ba2dbdaa8fa29b4810b1d6a3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="bdc-model-design-tools-overview"></a>Visão geral de ferramentas de design do modelo BDC
  Você pode criar um modelo de conectividade de dados de negócios (BDC) usando o Designer de BDC, o **detalhes de método BDC** janela e o **Explorer BDC**.  
  
 O **Explorer BDC** permite procurar o modelo, o modelo de pesquisa e definir descritores de tipo.  
  
## <a name="bdc-designer"></a>Designer BDC  
 O Designer de BDC permite definir as entidades no modelo e organizar visualmente suas relações com uma outra. Use o Designer de BDC para realizar as seguintes tarefas:  
  
-   Adicione entidades no modelo.  
  
-   Remova entidades do modelo.  
  
-   Defina relações entre entidades.  
  
 Para abrir o Designer de BDC, duas vezes no arquivo de modelo em seu projeto, ou abra o menu de atalho para o arquivo de modelo e, em seguida, escolha **abrir**. Adicionar uma entidade no modelo arrastando ou copiando um **entidade** do **caixa de ferramentas** no designer. Para criar uma associação entre duas entidades, escolha o **associação** controlar o **caixa de ferramentas**, escolha a entidade de primeiro e, em seguida, escolha a segunda entidade.  
  
## <a name="bdc-method-details-window"></a>Janela de detalhes de método BDC  
 Use o **detalhes de método BDC** janela para definir os parâmetros, instâncias e descritores de um método de filtro.  
  
 Você pode gerar rapidamente o localizador de localizador específico, criador, Updater, métodos e Deleter no **detalhes de método BDC** janela. Quando você gerar esses métodos, o Visual Studio adiciona metadados, como parâmetros, instâncias e descritores de tipo para o método. Você pode modificar esses metadados para satisfazer o seu cenário específico.  
  
 Para abrir o **detalhes de método BDC** janela, na barra de menus, escolha **exibição**, **outras janelas**, **detalhes de método BDC**.  
  
 Para exibir os métodos de **detalhes de método BDC** janela, escolha a entidade no Designer de BDC. Os métodos da entidade selecionada aparecem no **detalhes de método BDC** janela. Se você não escolher uma entidade no Designer de BDC, o **detalhes de método BDC** janela não exibe nenhuma informação.  
  
 Expandir ou recolher nós o **detalhes de método BDC** janela para definir parâmetros, instâncias e os descritores de filtro. Use o **Explorer BDC** para definir os descritores de tipo.  
  
## <a name="bdc-explorer"></a>BDC Explorer  
 O **Explorer BDC** exibe os elementos que compõem o modelo. Para abrir o **Explorer BDC**, na barra de menus, escolha **exibição**, **outras janelas**, **Explorer BDC**. Para procurar o modelo, expanda nós no **Explorer BDC**. Cada nó representa um elemento no XML do arquivo de modelo.  
  
 Como escolher nós o **BDC Explorer**, as propriedades de cada nó que você escolher aparecem no **propriedades** janela. Muitas dessas propriedades correspondem aos atributos no arquivo de modelo. Você pode procurar o modelo usando a caixa de pesquisa na parte superior do **Explorer BDC**.  
  
> [!NOTE]  
>  O **Explorer BDC** não exibe identificadores, as propriedades personalizadas, cadeias de caracteres localizadas, os grupos de associação, ações, descritores de filtros, listas de controle de ação e os valores de parâmetro padrão.  
  
### <a name="defining-type-descriptors"></a>Definindo descritores de tipo  
 Use o **Explorer BDC** para definir os descritores de tipo. O Gerenciador de BDC permite definir um descritor de tipo de uma vez e, em seguida, reutilizar esse descritor de tipo em outro lugar no seu modelo. Para fazer isso, um descritor de tipo de copiar e colá-la em qualquer outro parâmetro ou descritor de tipo.  
  
> [!NOTE]  
>  Alterações em um descritor de tipo original não afetam as cópias do descritor desse tipo.  
  
 Para obter mais informações, consulte [como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Como: adicionar uma entidade em um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Como: adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Como: adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Como: adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Como: adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Como: adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Criando uma associação entre entidades](../sharepoint/creating-an-association-between-entities.md)   
 [Passo a passo: Criando uma lista externa no SharePoint usando dados de negócios](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrando dados corporativos no SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Designando um modelo de Conectividade de Dados Corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  