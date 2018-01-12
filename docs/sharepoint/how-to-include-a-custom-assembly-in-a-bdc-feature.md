---
title: 'Como: incluir um Assembly personalizado em um recurso BDC | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 32554a0456c34a3c8b1d96c471fd7ae8e9221943
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Como incluir um assembly personalizado em uma funcionalidade BDC
  Seu projeto pode fazer referência a assemblies de outros projetos na mesma solução. No entanto, você deve adicionar esses assemblies para o arquivo de recurso do projeto usando o **atribuir referenciado assemblies LobSystems** caixa de diálogo.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Para incluir um assembly personalizado em um recurso de conectividade de dados de negócios (BDC)  
  
1.  Em **Solution Explorer**, escolha a pasta que contém o modelo BDC.  
  
2.  Sobre o **exibição** menu, clique em **janela propriedades**.  
  
3.  No **propriedades** janela, escolha o **Assemblies** propriedade e, em seguida, no botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET para dispositivos móveis Elipse de Designer")).  
  
     O **atribuir referenciado assemblies LobSystems** caixa de diálogo é exibida.  
  
4.  No **selecione um Assembly** , escolha o assembly personalizado.  
  
    > [!NOTE]  
    >  Assemblies são exibidas somente no **atribuir referenciado assemblies LobSystems** caixa de diálogo se você tiver adicionado uma referência ao projeto que contém o assembly. Para obter mais informações, consulte [como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  No **propriedades da referência** de grupo, abra a lista que aparece para o **escopo LobSystem** propriedade, escolha o sistema LOB dos métodos que usam o assembly personalizado e, em seguida, escolha o **Okey**  botão.  
  
    > [!NOTE]  
    >  Para depurar o código no assembly personalizado, você deve adicionar o assembly para o pacote de solução. Para obter mais informações, consulte [como: adicionar e remover Assemblies adicionais](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: usar um arquivo de recurso para especificar nomes localizados, propriedades e permissões](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Como: adicionar um arquivo de modelo BDC existente a um projeto do SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Como: criar um modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  