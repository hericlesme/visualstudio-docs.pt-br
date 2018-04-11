---
title: Tarefa FindAppConfigFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 5
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fd77102f1fcee56cb690dc5934dcf158763bd9f2
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="findappconfigfile-task"></a>Tarefa FindAppConfigFile
Localiza o arquivo app.config, se houver, nas listas fornecidas.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `FindAppConfigFile`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AppConfigFile`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica o primeiro item correspondente encontrado na lista, se houver.|  
|`PrimaryList`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica a lista principal pela qual pesquisar.|  
|`SecondaryList`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica a lista secundária pela qual pesquisar.|  
|`TargetPath`|Parâmetro `String` obrigatório.<br /><br /> Especifica o valor a ser adicionado como metadados.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)