---
title: Como referenciar o nome ou local do arquivo de projeto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7a688473b4657d905397d4798451b4860578ef0d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Como referenciar o nome ou local do arquivo de projeto
Você pode usar o nome ou local do projeto no próprio arquivo de projeto sem ter de criar sua própria propriedade. O [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornece propriedades reservadas que referenciam o nome do arquivo de projeto e outras propriedades relacionadas ao projeto. Para obter mais informações sobre propriedades reservadas, consulte [Propriedades reservadas e conhecidas do MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Usar a propriedade MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornece algumas propriedades reservadas que você pode usar em seus arquivos de projeto sem precisar defini-las todas as vezes. Por exemplo, a propriedade reservada `MSBuildProjectName` fornece uma referência ao nome do arquivo de projeto.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Para usar a propriedade MSBuildProjectName  
  
-   Faça referência à propriedade no arquivo de projeto com a notação $(), como faria com qualquer propriedade. Por exemplo:  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 Uma vantagem de usar uma propriedade reservada é que qualquer alteração no nome do arquivo de projeto é incorporada automaticamente. Na próxima vez que você compilar o projeto, o arquivo de saída terá o novo nome sem necessidade de ação adicional de sua parte.  
  
> [!NOTE]
>  As propriedades reservadas não podem ser redefinidas no arquivo de projeto.  
  
## <a name="example"></a>Exemplo  
 O arquivo de projeto de exemplo a seguir faz referência ao nome de projeto como uma propriedade reservada para especificar o nome para a saída.  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
[MSBuild](../msbuild/msbuild.md)  
 [Propriedades reservadas e conhecidas do MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)