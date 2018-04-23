---
title: Elemento ProjectSubType (modelos do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4414d5f444613996312978e9033145c6b8d3d82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Elemento ProjectSubType (modelos do Visual Studio)
Classifica o modelo em uma subcategoria do valor especificado no `ProjectType` elemento.  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Categoriza o modelo e define como ele exibe em um a **novo projeto** ou **Adicionar Novo Item** caixa de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 Esse valor Especifica a subcategoria do modelo.  
  
## <a name="remarks"></a>Comentários  
 O `ProjectSubType` é um elemento filho opcional de `TemplateData`.  
  
 O `ProjectSubType` elemento fornece uma subcategoria para o [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elemento. Esse valor pode incluir:  
  
-   `SmartDevice-NETCFv1`: Especifica que os destinos de modelo de [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versão 1.0.  
  
-   `SmartDevice-NETCFv2`: Especifica que os destinos tempalate o [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versão 2.0.  
  
 Se um modelo contém uma `ProjectType` elemento com um valor de `Web`, o `ProjectSubType` elemento Especifica a linguagem de programação do modelo. Esse elemento pode ter os seguintes valores:  
  
-   `CSharp`: Especifica que o modelo cria um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projeto Web ou item.  
  
-   `VisualBasic`: Especifica que o modelo cria um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeto Web ou item.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra os metadados para um modelo de projeto para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] segmentação do aplicativo de dispositivo de [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versão 2.0.  
  
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