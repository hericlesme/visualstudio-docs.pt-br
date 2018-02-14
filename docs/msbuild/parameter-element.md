---
title: "Elemento de parâmetro| Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1ae8927c8a8f3a3fcd3f57075de281e3ee0679a1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="parameter-element"></a>Elemento de parâmetro
Contém informações sobre um parâmetro específico de uma tarefa que é gerada por um `UsingTask``TaskFactory`.  O nome do elemento é o nome do parâmetro.  Para obter mais informações, consulte [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  

## <a name="syntax"></a>Sintaxe  

```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  

|Atributo|Descrição|  
|---------------|-----------------|  
|`ParameterType`|Atributo opcional.<br /><br /> O tipo .NET do parâmetro, por exemplo, "System.String".|  
|`Output`|Atributo booliano opcional.<br /><br /> Se `true`, esse parâmetro será um parâmetro de saída para a tarefa. Por padrão, o valor é `false`.|  
|`Required`|Atributo booliano opcional.<br /><br /> Se `true`, esse parâmetro será um parâmetro necessário para a tarefa. Por padrão, o valor é `false`.|  

### <a name="child-elements"></a>Elementos filho  
 nenhuma.  

### <a name="parent-elements"></a>Elementos pai  

|Elemento|Descrição|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contém uma lista opcional de parâmetros que estarão presentes na tarefa que é gerada por um `UsingTask``TaskFactory`.|  

## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o elemento `Parameter`.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)
