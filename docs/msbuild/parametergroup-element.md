---
title: Elemento ParameterGroup| Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ed99b0e7dbccbee99dbc290d79d2b25b9c84874
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31578582"
---
# <a name="parametergroup-element"></a>Elemento ParameterGroup
Contém uma lista opcional de parâmetros que estarão presentes na tarefa que é gerada por um `UsingTask``TaskFactory`. Para obter mais informações, consulte [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  

## <a name="syntax"></a>Sintaxe  

```  
<ParameterGroup />  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  
 nenhuma.  

### <a name="child-elements"></a>Elementos filho  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Parâmetro](../msbuild/parameter-element.md)|Contém informações sobre um parâmetro específico de uma tarefa que é gerada por um `UsingTask``TaskFactory`. O nome do elemento é o nome do parâmetro.|  

### <a name="parent-elements"></a>Elementos pai  

|Elemento|Descrição|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Fornece uma maneira para registrar tarefas em [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Pode ser que não haja nenhum ou mais de um elemento `UsingTask` em um projeto.|  

## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o elemento `ParameterGroup`.  

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
