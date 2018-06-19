---
title: Elemento LocationField (modelos de projeto do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0877d374317e3a7142996b012ff6abefc6b94724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138753"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Elemento LocationField (modelos de projeto do Visual Studio)
Especifica se ou não o **local** caixa de texto de **novo projeto** caixa de diálogo está habilitada, desabilitada ou ocultada para o modelo de projeto.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<LocationField >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Categoriza o modelo e define como ele exibe em ambos os **novo projeto**.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 Os valores de texto válidos são:  
  
-   `Enabled`, que especifica que o **local** caixa do **novo projeto** caixa de diálogo está habilitada.  
  
-   `Disabled`, que especifica que o **local** caixa do **novo projeto** caixa de diálogo está desabilitada.  
  
-   `Hidden`, que especifica que o **local** caixa do **novo projeto** caixa de diálogo está oculto.  
  
## <a name="remarks"></a>Comentários  
 O valor padrão é `Enabled`.  
  
 O **local** caixa de texto de **novo projeto** caixa de diálogo permite que os usuários alterem o diretório padrão no qual novos projetos são salvos.  
  
 O valor especificado no `Location` elemento será considerado somente pela caixa de diálogo se o sistema de projeto subjacente oferece suporte a ele.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os metadados para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modelo.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
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