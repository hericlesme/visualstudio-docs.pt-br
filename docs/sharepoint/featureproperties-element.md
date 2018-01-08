---
title: Elemento FeatureProperties | Microsoft Docs
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
helpviewer_keywords: FeatureProperties element
ms.assetid: 89233274-a842-4f40-a81a-5548379f6f39
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a8de1da87ce4c6ce88c19c8c9c4eda361ba421f4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="featureproperties-element"></a>Elemento FeatureProperties
  Representa uma coleção de valores de propriedade que são incluídos com um recurso quando ele é implantado no SharePoint. Após a implantação de um recurso, você pode acessar os valores de propriedade em seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Elemento opcional.<br /><br /> Representa uma propriedade personalizada, em formato de chave/valor.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Item de projeto](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint. Este é o elemento raiz necessário do arquivo. spdata.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre as propriedades do recurso, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informações do elemento  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|  
|**Arquivo de validação**|ProjectItemModelSchema.xsd|  
|**Pode estar vazio**|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de Item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fornecendo informações de pacote e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  