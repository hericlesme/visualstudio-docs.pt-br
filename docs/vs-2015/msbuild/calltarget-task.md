---
title: Tarefa CallTarget | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d12fde1654c4645a6b543e44f8c48f273f32349b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473239"
---
# <a name="calltarget-task"></a>Tarefa CallTarget
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tarefa CallTarget](https://docs.microsoft.com/visualstudio/msbuild/calltarget-task).  
  
  
Invoca os destinos especificados no arquivo de projeto.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `CallTarget`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Parâmetro de saída `Boolean` opcional.<br /><br /> Se `true`, o mecanismo [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] será chamado uma vez por destino. Se `false`, o mecanismo [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] será chamado para compilar todos os destinos. O valor padrão é `false`.|  
|`TargetOutputs`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém as saídas de todos os destinos compilados.|  
|`Targets`|Parâmetro `String[]` opcional.<br /><br /> Especifica o destino ou os destinos que serão compilados.|  
|`UseResultsCache`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, o resultado em cache será retornado, se presente.<br /><br /> **Observação** Quando uma tarefa MSBuild for executada, a saída é armazenada em cache em um escopo (ProjectFileName, GlobalProperties)[TargetNames] como uma lista de itens de build.|  
  
## <a name="remarks"></a>Comentários  
 Se um destino especificado em `Targets` falhar e `RunEachTargetSeparately` for `true`, a tarefa continuará a compilar os destinos restantes.  
  
 Se você deseja compilar destinos padrão, use a [Tarefa MSBuild](../msbuild/msbuild-task.md) e defina o parâmetro `Projects` como igual a `$(MSBuildProjectFile)`.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir chama `TargetA` de dentro de `CallOtherTargets`.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Destinos](../msbuild/msbuild-targets.md)



