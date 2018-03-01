---
title: Elemento ProjectType (modelos do Visual Studio) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 46f9f748f683558e6fb82607d4c87a0a0dbc1cae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="projecttype-element-visual-studio-templates"></a>Elemento ProjectType (modelos do Visual Studio)
Categoriza o modelo de projeto para que ele apareça no grupo especificado no **novo projeto** ou **Adicionar Novo Item** caixa de diálogo.  
  
> [!WARNING]
>  Modelos de projeto têm suporte do C++ a partir do Visual Studio 2012. Eles não têm suporte para C++ no Visual Studio 2010 e versões anteriores.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele exibe em um a **novo projeto** ou **Adicionar Novo Item** caixa de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 Esse valor Especifica o tipo de projeto de modelo criará e deve conter um dos seguintes valores:  
  
-   `CSharp`: Especifica que o modelo cria um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projeto ou item.  
  
-   `VisualBasic`: Especifica que o modelo cria um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeto ou item.  
  
-   `Web`: Especifica que o modelo cria um projeto da Web ou um item. Se o `ProjectType` elemento contém esse valor, o idioma do projeto ou item for definido no [elemento ProjectSubType (modelos do Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Comentários  
 O `ProjectType` é um elemento filho obrigatório de `TemplateData`.  
  
 O valor da `ProjectType` elemento Especifica onde o modelo está localizado no **novo projeto** ou **Adicionar Novo Item** caixa de diálogo. Por exemplo, um modelo com um `ProjectType` valor de `CSharp` aparece sob o **Visual C#** nó o **novo projeto** caixa de diálogo.  
  
 Um subtipo do modelo pode ser especificado usando o [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra os metadados para um modelo de projeto para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicativo.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
 [Elemento ProjectSubType (Modelos do Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)