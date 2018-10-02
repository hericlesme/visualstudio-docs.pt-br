---
title: BuildProjectOnLoad (modelos do Visual Studio) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- <BuildOnLoad> element [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76576e37ab63ca42f94cb5d7fb51a3bf967fdbc5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466419"
---
# <a name="buildprojectonload-visual-studio-templates"></a>BuildProjectOnLoad (Modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [BuildProjectOnLoad (modelos do Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/buildprojectonload-visual-studio-templates).  
  
Especifica se deve compilar o projeto imediatamente após sua criação.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<BuildProjectOnLoad>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido em qualquer um de **novo projeto** ou o **Adicionar Novo Item** caixa de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 O texto deve ser `true` ou `false`, que indica se é compilar o projeto imediatamente após sua criação.  
  
## <a name="remarks"></a>Comentários  
 `BuildProjectOnLoad` é um atributo opcional. O valor padrão é `false`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os metadados para um [!INCLUDE[csprcs](../includes/csprcs-md.md)] modelo.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <BuildProjectOnload>true</BuildProjectOnLoad>  
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
 [Elemento TemplateContent (modelos do Visual Studio)](../extensibility/templatecontent-element-visual-studio-templates.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)   
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

