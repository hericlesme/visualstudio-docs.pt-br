---
title: Referência de esquema de Item de projeto do SharePoint | Microsoft Docs
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
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b039b1cf31a04a24819b03114c661a3ab1b108a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint Referência do esquema de item de projeto
  Visual Studio usa o esquema de item de projeto do SharePoint para validar o conteúdo de arquivos. spdata. Um arquivo. spdata Especifica o conteúdo e o comportamento de um item de projeto do SharePoint. Para obter mais informações sobre o conteúdo do SharePoint dos itens de projeto, consulte [criando modelos de Item e modelos de projeto do SharePoint para itens de projeto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 O esquema de item de projeto do SharePoint é denominado ProjectItemModelSchema.xsd e é instalado por padrão em % arquivos de programas (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.  
  
 O elemento raiz é o [ProjectItem](../sharepoint/projectitem-element.md) elemento. A tabela a seguir descreve todos os elementos definidos pelo esquema.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa uma coleção de itens de dados personalizados que são associados ao item de projeto do SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Representa um item de dados personalizado que é associado ao item de projeto do SharePoint, no formato de chave/valor. A chave e o valor devem ser cadeias de caracteres.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Representa uma coleção de valores de propriedade que são incluídos com um recurso quando ele é implantado no SharePoint. Após a implantação de um recurso, você pode acessar os valores de propriedade em seu código.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Representa uma propriedade personalizada que está incluída com um recurso quando ele é implantado no SharePoint. Após a implantação de um recurso, você pode acessar a propriedade em seu código.|  
|[Arquivos](../sharepoint/files-element.md)|Especifica os arquivos para implantar com o item de projeto do SharePoint, como um arquivo de elemento de recurso ou a saída de um projeto.|  
|[Item de projeto](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Representa um arquivo do SharePoint, como arquivo de elemento de recurso, para incluir o item de projeto quando ele é implantado no SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Representa uma pasta mapeada.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Representa a saída de um projeto para incluir o item de projeto quando ele é implantado no SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Representa um controle ASPX ou a Web Part é considerada segura para qualquer usuário acesse qualquer página ASPX no site do SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa uma coleção de controles ASPX e Web Parts que são designados como seguro para qualquer usuário acesse qualquer página ASPX no site do SharePoint.|  
  
## <a name="see-also"></a>Consulte também  
 [Criando modelos de item e de projeto para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  