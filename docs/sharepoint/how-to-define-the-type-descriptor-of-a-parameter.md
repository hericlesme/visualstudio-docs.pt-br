---
title: 'Como: definir o descritor de tipo de um parâmetro | Microsoft Docs'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6ebdd8e968d631cf1d53515449c7e705c2978087
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Como definir o descritor de tipo de um parâmetro
  Um descritor de tipo contém propriedades que descrevem o tipo de dados de um parâmetro. Um descritor de tipo pode definir um campo, uma entidade ou uma coleção de entidades. Para obter mais informações, consulte [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Para definir o descritor de tipo de um parâmetro  
  
1.  No **detalhes de método BDC** janela, escolha o descritor do tipo do parâmetro.  
  
2.  Na barra de menus, escolha **exibição**, **janela propriedades**.  
  
3.  No **propriedades** janela, defina as propriedades do descritor de tipo.  
  
     Os procedimentos a seguir descrevem como definir um descritor de tipo como uma coleção de entidades, entidade ou campo.  
  
### <a name="to-define-a-field"></a>Para definir um campo  
  
1.  No **propriedades** janela, defina o **nome** propriedade do descritor de tipo para o nome de um campo no tipo que representa a entidade (por exemplo: **FirstName**).  
  
2.  Na lista ao lado de **TypeName** propriedade, escolha o tipo de dados apropriado (por exemplo, **Int32**).  
  
     Para obter informações sobre outros parâmetros opcionais, consulte [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-an-entity"></a>Para definir uma entidade  
  
1.  No **propriedades** janela, defina o **nome** propriedade para um nome que descreve a entidade (por exemplo: **contato**).  
  
2.  Definir o **TypeName** propriedade para o nome totalmente qualificado do tipo que representa a entidade. Esse tipo pode ser uma classe em seu projeto, um tipo definido em um assembly referenciado em sua solução ou um tipo definido no modelo de objeto BDC.  
  
    -   Para uma classe em seu projeto, escolha a seta para baixo ao lado de **TypeName** propriedade, escolha o **projeto atual** guia na caixa de diálogo que aparece e, em seguida, escolha a classe em seu projeto.  
  
         O nome totalmente qualificado inclui o namespace e o nome da classe seguida do nome do sistema LOB. O exemplo a seguir define o valor de **TypeName** propriedade a uma classe em seu projeto.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Para um tipo localizado em um assembly em sua solução, o nome totalmente qualificado inclui o nome do tipo, o nome do assembly, o número de versão, a cultura e token de chave pública.  
  
         O exemplo a seguir define o valor de **TypeName** propriedade para um tipo definido em um assembly referenciado em sua solução.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Para um tipo definido no modelo de objeto BDC, o nome totalmente qualificado inclui o namespace e o nome do tipo.  
  
         O exemplo a seguir define o valor da **TypeName** propriedade para um tipo no modelo de objeto BDC.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  No **detalhes de método BDC** janela, abra a lista que aparece para o descritor de tipo e, em seguida, escolha **editar**.  
  
     O **BDC Explorer** janela será aberta.  
  
4.  No **Explorer BDC**, abra o menu de atalho do descritor de tipo e, em seguida, escolha **Adicionar descritor de tipo**.  
  
     Um novo descritor de tipo é adicionado como um filho ao descritor de tipo de entidade. Configure o descritor do tipo como um campo.  
  
5.  Repita a etapa 4 para adicionar um descritor de tipo filho para cada campo da entidade.  
  
### <a name="to-define-a-collection-of-entities"></a>Para definir uma coleção de entidades  
  
1.  No **detalhes de método BDC** janela, escolha o descritor do tipo do parâmetro que você deseja.  
  
2.  Na barra de menus, escolha **exibição**, **janela propriedades**.  
  
3.  No **propriedades** janela, defina o **nome** propriedade para um nome que descreve a entidade (por exemplo: **contatos**).  
  
4.  Definir o **IsCollection** propriedade **True**. Isso indica que esse descritor de tipo é uma coleção de entidades.  
  
5.  Definir o **TypeName** propriedade como uma cadeia de caracteres que contém uma referência para o <xref:System.Collections.Generic.IEnumerable%601> interface e o nome totalmente qualificado do tipo que representa a entidade. Esse tipo pode ser uma classe em seu projeto, um tipo definido em um assembly referenciado em sua solução ou um tipo definido no modelo de objeto BDC.  
  
    -   Para uma classe em seu projeto, escolha a seta para baixo ao lado de **TypeName** propriedade, escolha o **projeto atual** guia na caixa de diálogo que aparece e, em seguida, escolha a classe em seu projeto.  
  
         O nome totalmente qualificado inclui o namespace e o nome da classe seguida do nome do sistema LOB.  
  
         O exemplo a seguir define o valor de **TypeName** propriedade a uma coleção de classes no seu projeto.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1]'  
  
    -   Para um tipo localizado em um assembly em sua solução, o nome totalmente qualificado inclui o nome do tipo, o nome do assembly, o número de versão, a cultura e token de chave pública.  
  
         O exemplo a seguir define o valor da **TypeName** propriedade a uma coleção de tipos em um assembly referenciado em sua solução.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, versão = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089]'  
  
    -   Para um tipo definido no modelo de objeto BDC, o nome totalmente qualificado inclui apenas o namespace e o nome do tipo.  
  
         O exemplo a seguir define o valor de **TypeName** propriedade a uma coleção de tipos definidos no modelo de objeto BDC.  
  
         `System.Collections.Generic.IEnumerable`1 [DynamicType]'  
  
6.  No **detalhes de método BDC** janela, abra a lista que aparece para o descritor de tipo e, em seguida, escolha **editar**.  
  
     O **BDC Explorer** janela será aberta.  
  
7.  No **Explorer BDC**, abra o menu de atalho do descritor de tipo e, em seguida, escolha **Adicionar descritor de tipo**.  
  
     Um novo descritor de tipo é adicionado como um filho ao descritor de tipo de coleção. Configure o descritor do tipo como uma entidade.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Como: adicionar uma entidade em um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como: definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)   
 [Designando um modelo de Conectividade de Dados Corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  