---
title: Elemento ProjectItemFile | Microsoft Docs
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
helpviewer_keywords: ProjectItemFile element
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 023d2f64dc3f05d518add1cd4bf6c3415f435985
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="projectitemfile-element"></a>Elemento ProjectItemFile
  Representa um arquivo do SharePoint, como arquivo de elemento de recurso, para incluir o item de projeto quando ele é implantado no SharePoint.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**Source**|Necessário **xs: string** atributo.<br /><br /> O nome do arquivo para implantar com o item de projeto.|  
|**Target**|Opcional **xs: string** atributo.<br /><br /> O caminho onde o arquivo será implantado no SharePoint, relativo à pasta raiz de implantação. A pasta raiz de implantação é determinada pelo tipo de implantação especificado pelo **tipo** atributo. Se o **destino** atributo não for especificado, o arquivo será implantado em uma pasta com o nome especificado no **fonte** atributo.<br /><br /> Para obter mais informações, consulte as descrições para o **caminho de implantação** e **raiz de implantação** propriedades do SharePoint itens de projeto do [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Tipo**|Necessário **xs: string** atributo.<br /><br /> O tipo de implantação para o arquivo. Para obter mais informações sobre os valores possíveis, consulte a descrição para o **tipo de implantação** propriedades de itens de projeto do SharePoint no [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Arquivos](../sharepoint/files-element.md)|Especifica os arquivos a serem incluídos com o item de projeto do SharePoint quando ele é implantado no SharePoint.|  
  
## <a name="remarks"></a>Comentários  
 Arquivos do SharePoint que normalmente são referenciados na **ProjectItemFile** elementos incluem arquivos de elemento de recurso (Elements), arquivos de esquema para definições de lista (Schema.xml) e arquivos de definição de Web Part para Web Parts (. WebPart).  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|  
|**Arquivo de validação**|ProjectItemModelSchema.xsd|  
|**Pode estar vazio**|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência do esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  