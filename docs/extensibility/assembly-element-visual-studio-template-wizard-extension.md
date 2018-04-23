---
title: Elemento Assembly (extensão de Assistente de modelo do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1610df76bfce303bd13c69cb8298ac62106fd7e6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>Elemento de assembly (Extensão do Assistente de Modelo do Visual Studio)
Especifica o nome ou o nome forte do assembly que implementa o `IWizard` interface.  
  
 \<VSTemplate >  
\<WizardExtension >  
\<Assembly >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Assembly>AssemblyName</Assembly>  
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contém os elementos de registro para personalizar o Assistente de modelo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 Esse texto Especifica o assembly que implementa o `IWizard` interface. Esse nome de assembly deve ser especificado como um nome completo do assembly. Por exemplo, `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`.  
  
## <a name="remarks"></a>Comentários  
 O `Assembly` é um elemento filho obrigatório de `WizardExtension`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os metadados para o modelo de projeto padrão para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicativo do Windows.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs</ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)   
 [Como usar assistentes com modelos do projeto](../extensibility/how-to-use-wizards-with-project-templates.md)