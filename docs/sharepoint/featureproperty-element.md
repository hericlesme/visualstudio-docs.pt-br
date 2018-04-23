---
title: Elemento FeatureProperty | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 41493e44ee0a82a09cf000eb056f686ff7b4d1bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="featureproperty-element"></a>Elemento FeatureProperty
  Representa uma propriedade personalizada que está incluída com um recurso quando ele é implantado no SharePoint. Após a implantação de um recurso, você pode acessar a propriedade em seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**Chave**|Necessário **xs: string** atributo.<br /><br /> A chave é usada para armazenar e recuperar o valor da propriedade. Cada propriedade deve ter uma chave que é exclusiva dentro do recurso.|  
|**Value**|Necessário **xs: string** atributo.<br /><br /> O valor da propriedade.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Representa uma coleção de valores de propriedade que são incluídos com um recurso quando ele é implantado no SharePoint.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre as propriedades do recurso, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|  
|**Arquivo de validação**|ProjectItemModelSchema.xsd|  
|**Pode estar vazio**|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de Item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fornecendo informações de pacote e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  