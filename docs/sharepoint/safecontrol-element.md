---
title: Elemento SafeControl | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 7458120d7a130de96a1a271c83e5376fe94481f3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="safecontrol-element"></a>Elemento SafeControl
  Representa um controle ASPX ou a Web Part é considerada segura para qualquer usuário acesse qualquer página ASPX no site do SharePoint.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**Assembly**|Opcional **xs: string** atributo.<br /><br /> O nome do assembly no qual o controle ASPX ou a Web Part está definida. Por padrão, esse atributo usa o **$SharePoint.Project.AssemblyFullName$** parâmetro substituível para o nome do assembly. Para obter mais informações, consulte [parâmetros substituíveis](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Opcional **xs: Boolean** atributo.<br /><br /> Especifica se a Web Part ou controle ASPX é segura para os usuários não confiáveis acessem.|  
|**IsSafeAgainstScript**|Opcional **xs: Boolean** atributo.<br /><br /> Especifica se os usuários não confiáveis podem exibir ou editar as propriedades do controle ASPX ou Web Part.|  
|**Nome**|Opcional **xs: string** atributo.<br /><br /> O nome desta entrada de controle de segurança na coleção.|  
|**Namespace**|Opcional **xs: string** atributo.<br /><br /> O namespace do controle ASPX ou Web Part.|  
|**TypeName**|Opcional **xs: string** atributo.<br /><br /> O nome do tipo do controle ASPX ou Web Part.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa uma coleção de controles ASPX e Web Parts que são designados como seguro para qualquer usuário acesse qualquer página ASPX no site do SharePoint.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre controles de seguras, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
  
  