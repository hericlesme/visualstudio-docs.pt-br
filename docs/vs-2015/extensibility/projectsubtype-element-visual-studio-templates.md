---
title: Elemento ProjectSubType (modelos do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3b51174948104dd8e5bf67d90f967f028cc6773
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464007"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Elemento ProjectSubType (modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [elemento ProjectSubType (modelos do Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/projectsubtype-element-visual-studio-templates).  
  
Classifica o modelo em uma subcategoria de valor especificado no `ProjectType` elemento.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Categoriza o modelo e define como ele é exibido em qualquer um de **novo projeto** ou o **Adicionar Novo Item** caixa de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 Esse valor Especifica a subcategoria do modelo.  
  
## <a name="remarks"></a>Comentários  
 O `ProjectSubType` é um elemento filho opcional de `TemplateData`.  
  
 O `ProjectSubType` elemento fornece uma subcategoria para a [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elemento. Esse valor pode incluir:  
  
-   `SmartDevice-NETCFv1`: Especifica que os destinos de modelo a [!INCLUDE[Compact](../includes/compact-md.md)] versão 1.0.  
  
-   `SmartDevice-NETCFv2`: Especifica que os destinos tempalate o [!INCLUDE[Compact](../includes/compact-md.md)] versão 2.0.  
  
 Se um modelo contém um `ProjectType` elemento com um valor de `Web`, o `ProjectSubType` elemento Especifica a linguagem de programação do modelo. Esse elemento pode ter os seguintes valores:  
  
-   `CSharp`: Especifica que o modelo cria um [!INCLUDE[csprcs](../includes/csprcs-md.md)] projeto da Web ou um item.  
  
-   `VisualBasic`: Especifica que o modelo cria um [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeto da Web ou um item.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra os metadados para um modelo de projeto para um [!INCLUDE[csprcs](../includes/csprcs-md.md)] segmentação do aplicativo de dispositivo a [!INCLUDE[Compact](../includes/compact-md.md)] versão 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)   
 [Elemento ProjectType (Modelos do Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)

