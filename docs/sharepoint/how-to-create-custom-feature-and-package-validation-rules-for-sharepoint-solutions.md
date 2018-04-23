---
title: 'Como: criar funcionalidade personalizada e regras de validação de pacote para soluções do SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c68df756e24fc45603d34dd6982a09889bd5203
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Como criar funcionalidade personalizada e regras de validação de pacote para soluções do SharePoint
  Você pode criar regras de validação personalizada para verificar se o pacote de solução gerado pelo Visual Studio. Você pode executar a validação completa em um recurso inteiro ou um pacote, selecionando **validar** no menu de contexto de um pacote ou o recurso de **PackagingExplorer**. Validação parcial é executada quando você adicionar novos itens de projeto SharePonit ou recursos para o projeto para determinar se o pacote ou o recurso seria em um estado válido.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Para criar uma regra de validação de pacote personalizado  
  
1.  Crie um projeto de biblioteca de classes.  
  
2.  Adicione referências aos assemblies a seguir:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Crie uma classe que implementa uma das seguintes interfaces:  
  
    -   Para criar uma regra de validação de pacote, implementar a <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interface.  
  
    -   Para criar uma regra de validação de recurso, implementar a <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interface.  
  
4.  Adicionar o <xref:System.ComponentModel.Composition.ExportAttribute> à classe. Este atributo permite que o Visual Studio descobrir e carregar sua regra de validação. Passar o <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> ou <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> tipo para o construtor de atributo.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como criar uma regra de validação de recurso personalizada.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar a extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  