---
title: Elemento ExtensionData | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b579a0221fcba04e2ca0915957f2bdbf60b91d84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="extensiondata-element"></a>Elemento ExtensionData
  Representa uma coleção de itens de dados personalizados que são associados ao item de projeto do SharePoint.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Elemento opcional.<br /><br /> Representa um item de dados personalizado que é associado ao item de projeto do SharePoint, no formato de chave/valor. A chave e o valor devem ser cadeias de caracteres.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Item de projeto](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint. Este é o elemento raiz necessário do arquivo. spdata.|  
  
## <a name="remarks"></a>Comentários  
 Quando você associa dados personalizados com um item de projeto do SharePoint usando o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> do objeto, o Visual Studio salva os dados para o **ExtensionData** elemento no arquivo. spdata para o item de projeto. Para obter mais informações, consulte [salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|  
|**Arquivo de validação**|ProjectItemModelSchema.xsd|  
|**Pode estar vazio**|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência do esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  