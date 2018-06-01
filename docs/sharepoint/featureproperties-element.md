---
title: Elemento FeatureProperties | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ee33d880a56103ea024f22038350ec36021561b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691782"
---
# <a name="featureproperties-element"></a>Elemento FeatureProperties
  Uma coleção de valores de propriedade que são incluídos com um recurso quando ele é implantado no SharePoint. Após a implantação de um recurso, você pode acessar os valores de propriedade em seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
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
|[Item de projeto](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint. Esse elemento, o elemento raiz necessário do `.spdata` arquivo.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre as propriedades do recurso, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informações do elemento  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|**Namespace**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>SharePointTools/2010/SharePointProjectItemModel|  
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|  
|**Arquivo de validação**|ProjectItemModelSchema.xsd|  
|**Pode estar vazio**|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de Item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fornecendo informações de pacote e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  