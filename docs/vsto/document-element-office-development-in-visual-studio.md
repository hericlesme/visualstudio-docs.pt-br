---
title: '&lt;documento&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
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
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3eeabc3d271e02b83530ffd15ff2e951defcc589
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;documento&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `document` elemento o `vstov4` namespace armazena informações específicas de personalização para personalizações no nível do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 Necessário apenas para personalizações no nível do documento. O `document` elemento o `vstov4` namespace. O `document` elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`solutionId`|Necessário. O GUID usado pelo Visual Studio Tools para Office runtime para identificar exclusivamente uma solução de nível de documento. Esse valor é armazenado como propriedade assemblylocation personalizada de documento. Para obter mais informações, consulte [visão geral de propriedades de documento personalizadas](../vsto/custom-document-properties-overview.md).|  
  
 `document`não possui elementos filho.  
  
## <a name="document-level-customization-example"></a>Exemplo de personalização de nível de documento  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir ilustra o `document` elemento em uma solução de nível de documento implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido em [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto de aplicativo ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  