---
title: Elemento ProjectItem (modelos de projeto do Visual Studio) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ca5143a3e5eaff488fee89b643a40adb60473bd8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Elemento ProjectItem (modelos de projeto do Visual Studio)
Especifica um arquivo que está incluído no modelo de projeto.  
  
> [!NOTE]
>  O `ProjectItem` elemento aceita atributos diferentes, dependendo se o modelo é para um projeto ou um item. Este tópico explica o `ProjectItem` elemento para modelos de projeto. Para obter uma explicação sobre o `ProjectItem` elemento para modelos de item, consulte [elemento ProjectItem (modelos de Item do Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<Item de projeto >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`TargetFileName`|Atributo opcional.<br /><br /> Especifica o nome e caminho do item de projeto quando um projeto é criado a partir do modelo. Esse atributo é útil para a criação de uma estrutura de diretórios diferentes da estrutura de diretório no modelo de arquivo. zip, ou para usar a substituição de parâmetro para criar um nome de item.|  
|`ReplaceParameters`|Atributo opcional.<br /><br /> Um valor booleano que especifica se o item possui valores de parâmetro devem ser substituídos quando um projeto é criado a partir do modelo. O valor padrão é `false`.|  
|`OpenInEditor`|Atributo opcional.<br /><br /> Um valor booleano que especifica se o item deve ser aberto no editor de respectivos em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando um projeto é criado a partir do modelo.<br /><br /> O `OpenInWebBrowser` e `OpenInHelpBrowser` atributos são ignorados em um item com um `OpenInEditor` valor `true`.<br /><br /> O valor padrão é `false`.|  
|`OpenInWebBrowser`|Atributo opcional.<br /><br /> Um valor booleano que especifica se o item deve ser aberto o navegador da Web quando um projeto é criado a partir do modelo.<br /><br /> Somente arquivos HTML e arquivos de texto que são locais para o projeto podem ser abertos no navegador da Web. URLs externas não podem ser abertos com esse atributo.<br /><br /> O valor padrão é `false`.|  
|`OpenInHelpBrowser`|Atributo opcional.<br /><br /> Um valor booleano que especifica se o item deve ser aberto no Visualizador da Ajuda quando um projeto é criado a partir do modelo.<br /><br /> Somente arquivos HTML e arquivos de texto que são locais para o projeto podem ser abertos no navegador. URLs externas não podem ser abertos com esse atributo.<br /><br /> O valor padrão é `false`.|  
|`OpenOrder`|Atributo opcional.<br /><br /> Especifica um valor numérico que representa a ordem que itens serão abertos em seus respectivos editores. Todos os valores devem ser múltiplos de 10. Itens com a maior `OpenOrder` valores são abertos pela primeira vez.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Projeto](../extensibility/project-element-visual-studio-templates.md)|Especifica os arquivos ou diretórios a serem adicionados ao projeto.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 Um `string` que representa o nome ou o caminho para um arquivo no arquivo. zip de modelo.  
  
## <a name="remarks"></a>Comentários  
 `ProjectItem`é um filho opcional de `Project`.  
  
 O `TargetFileName` atributo pode ser usado para criar uma estrutura de diretórios diferentes da estrutura de diretório no arquivo. zip de modelo. Por exemplo, se o arquivo `MyFile.vb` existe na raiz do arquivo. zip do modelo, mas você deseja que o arquivo será colocado em um diretório chamado `CustomFiles` em todos os projetos criados usando o modelo, você usaria o seguinte XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 O `TargetFileName` atributo também pode ser usado para renomear os arquivos que contêm caracteres internacionais em seus nomes de arquivos. Por exemplo, um arquivo. zip de modelo não pode conter nomes de arquivo com caracteres Unicode, para que o arquivo deve ser renomeado antes que ela pode ser compactada em um arquivo. zip. O `TargetFileName` atributo pode ser usado para definir o nome do arquivo para o nome de arquivo Unicode original.  
  
 O `TargetFileName` atributo também pode ser usado para renomear arquivos com parâmetros. O procedimento a seguir explica como renomear o arquivo `MyFile.vb`, que existe no diretório raiz do arquivo. zip do modelo, para um nome de arquivo com base no nome do projeto.  
  
### <a name="to-rename-files-with-parameters"></a>Para renomear arquivos com parâmetros  
  
1.  Use o seguinte XML no arquivo. vstemplate:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Abra o arquivo de projeto (. vbproj para um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeto) em um editor de texto ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Localize a linha no arquivo de projeto que é semelhante ao XML a seguir:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Substitua a linha de código XML a seguir:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Quando um projeto é criado com base neste modelo, o nome do arquivo se baseará o nome de usuário inserido na **novo projeto** caixa de diálogo, com todos os caracteres inseguros e espaços removidos. Para obter mais informações, consulte [parâmetros de modelo](../ide/template-parameters.md).  
  
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
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
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
 [Parâmetros de modelo](../ide/template-parameters.md)   
 [Elemento ProjectItem (Modelos de item do Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)