---
title: Tarefa RemoveDuplicates | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: "9"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2717ddb7622ee3f7cbaf5def7d1243e3a4800c19
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="removeduplicates-task"></a>Tarefa RemoveDuplicates
Remove itens duplicados da coleção do item especificado.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `RemoveDuplicates`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Filtered`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém uma coleção de itens com todos os itens duplicados removidos.|  
|`Inputs`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Coleção de itens do qual remover itens duplicados.|  
  
## <a name="remarks"></a>Comentários  
 Esta tarefa não diferencia maiusculas de minúsculas e não compara os metadados do item ao determinar as duplicatas.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `RemoveDuplicates` para remover itens duplicados da `MyItems` coleção de itens. Quando a tarefa for concluída, a coleção de item `FilteredItems` contém um item.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)