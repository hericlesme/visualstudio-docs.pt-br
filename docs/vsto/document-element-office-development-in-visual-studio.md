---
title: '&lt;documento&gt; elemento (desenvolvimento do Office no Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e33e638937a02589a08e3ba2bebf9d3e9aeb1a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
  
 `document` não possui elementos filho.  
  
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
  
  