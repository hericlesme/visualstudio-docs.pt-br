---
title: Elemento ExtensionDataItem | Microsoft Docs
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
helpviewer_keywords: ExtensionDataItem element
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 57e6d01e918256217e94077f6414651e50dd4c74
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="extensiondataitem-element"></a>Elemento ExtensionDataItem
  Representa um item de dados personalizado que é associado ao item de projeto do SharePoint, no formato de chave/valor. A chave e o valor devem ser cadeias de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**Chave**|Necessário **xs: string** atributo.<br /><br /> A chave é usada para armazenar e recuperar o item de dados.|  
|**Value**|Necessário **xs: string** atributo.<br /><br /> O valor do item de dados.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa uma coleção de itens de dados personalizados que são associados ao item de projeto do SharePoint.|  
  
## <a name="remarks"></a>Comentários  
 Quando você associa dados personalizados com um item de projeto do SharePoint usando o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> do objeto, o Visual Studio salva os dados para um novo **ExtensionDataItem** elemento no arquivo. spdata para o item de projeto. Para obter mais informações, consulte [salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|  
|**Arquivo de validação**|ProjectItemModelSchema.xsd|  
|**Pode estar vazio**|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência do esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  