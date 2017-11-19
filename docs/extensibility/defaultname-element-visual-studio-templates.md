---
title: Elemento DefaultName (modelos do Visual Studio) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords: DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0e65c17eef2242a8732638be680889ea9b55374
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="defaultname-element-visual-studio-templates"></a>Elemento DefaultName (modelos do Visual Studio)
Especifica o nome que o sistema de projeto do Visual Studio gerará para o projeto ou item quando ele é criado.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<DefaultName >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
  
 Esse texto Especifica o nome padrão do projeto ou item.  
  
## <a name="remarks"></a>Comentários  
 `DefaultName` é um elemento opcional.  
  
 Para projetos, este elemento Especifica o nome do diretório que armazena o projeto no disco. Para itens, especifica o nome do arquivo do arquivo de origem.  
  
 Quando você cria um projeto ou item, você pode modificar o nome padrão usando o **nome** opção, que está disponível em um a **novo projeto** caixa de diálogo ou **Adicionar Novo Item** caixa de diálogo.  
  
 Se você não deseja que o sistema de projeto para gerar o nome padrão para o projeto ou item, em seguida, defina o [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) elemento `False`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os metadados para o modelo de item padrão para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)