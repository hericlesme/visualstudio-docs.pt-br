---
title: Elemento ProjectItemFolder | Microsoft Docs
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
helpviewer_keywords: ProjectItemFolder element
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c6b5c895f36f3e0b040ce1e3db7cb87cd52e5b9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="projectitemfolder-element"></a>Elemento ProjectItemFolder
  Representa uma pasta mapeada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**Target**|Necessário **xs: string** atributo.<br /><br /> O caminho da pasta de instalação do SharePoint na pasta mapeada corresponde a, relativo à pasta raiz de implantação. A pasta raiz de implantação é determinada pelo tipo de implantação especificado pelo **tipo** atributo.<br /><br /> Para obter mais informações, consulte as descrições para o **caminho de implantação** e **raiz de implantação** propriedades do SharePoint itens de projeto do [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Tipo**|Necessário **xs: string** atributo.<br /><br /> O tipo de implantação para a pasta mapeada. Para obter mais informações sobre os valores possíveis, consulte a descrição para o **tipo de implantação** propriedades de itens de projeto do SharePoint no [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Item de projeto](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint. Este é o elemento raiz necessário do arquivo. spdata.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre pastas mapeadas, consulte [como: adicionar e remover pastas mapeadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|  
|**Arquivo de validação**|ProjectItemModelSchema.xsd|  
|**Pode estar vazio**|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de Item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Como adicionar e remover pastas mapeadas](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  