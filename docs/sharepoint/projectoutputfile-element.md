---
title: Elemento ProjectOutputFile | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f77cb92e62d5a5aec4d5e43fe295a3bab279c579
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692152"
---
# <a name="projectoutputfile-element"></a>Elemento ProjectOutputFile
  Representa a saída de um projeto separado para incluir com o item de projeto quando ele é implantado no SharePoint.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**projectId**|Necessário **xs: string** atributo.<br /><br /> O GUID do projeto dependente que tem a saída que você deseja incluir. Isso corresponde do **ProjectGuid** elemento no arquivo de projeto dependente.|  
|**ProjectPath**|Necessário **xs: string** atributo.<br /><br /> O caminho relativo, incluindo o nome de arquivo do projeto do projeto dependente que tem a saída que você deseja incluir. Esse caminho é relativo à pasta raiz do projeto do SharePoint que contém o item de projeto do SharePoint.|  
|**Target**|Opcional **xs: string** atributo.<br /><br /> O caminho onde a saída do projeto dependente deve ser implantado no servidor do SharePoint, relativo à pasta raiz de implantação. A pasta raiz de implantação é determinada pelo tipo de implantação especificado pelo **tipo** atributo.<br /><br /> Para obter mais informações, consulte as descrições para o **caminho de implantação** e **raiz de implantação** propriedades do SharePoint itens de projeto do [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Tipo**|Necessário **xs: string** atributo.<br /><br /> O tipo de implantação a ser usado para a saída do projeto dependente. Para obter mais informações sobre os valores possíveis, consulte a descrição para o **tipo de implantação** propriedades de itens de projeto do SharePoint no [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Arquivos](../sharepoint/files-element.md)|Especifica os arquivos a serem incluídos com o item de projeto do SharePoint quando ele é implantado no SharePoint.|  
  
## <a name="remarks"></a>Comentários  
 Use o **ProjectOutputFile** elemento para incluir na implantação do item de projeto do SharePoint, a saída de um projeto. Você pode especificar um projeto diferente, ou mesmo projeto que contém o item de projeto. Para obter mais informações, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|**Namespace**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>SharePointTools/2010/SharePointProjectItemModel|  
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|  
|**Arquivo de validação**|ProjectItemModelSchema.xsd|  
|**Pode estar vazio**|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de Item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fornecimento de empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  