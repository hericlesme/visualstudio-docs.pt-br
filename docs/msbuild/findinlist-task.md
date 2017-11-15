---
title: Tarefa FindInList | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: c30b667564b3ffc4852f39c5ccc96c6527720a1f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="findinlist-task"></a>Tarefa FindInList
Em uma lista especificada, localiza um item com o itemspec correspondente.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da [Tarefa FindInList](../msbuild/findinlist-task.md).  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`CaseSensitive`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a pesquisa diferencia maiúsculas de minúsculas; caso contrário, não diferencia. O valor padrão é `true`.|  
|`FindLastMatch`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, retorna a última correspondência; caso contrário, retorna a primeira correspondência. O valor padrão é `false`.|  
|`ItemFound`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> O primeiro item correspondente encontrado na lista, se houver.|  
|`ItemSpecToFind`|Parâmetro `String` obrigatório.<br /><br /> O itemspec pelo qual pesquisar.|  
|`List`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> A lista na qual pesquisar o itemspec.|  
|`MatchFileNameOnly`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, corresponde apenas com a parte do nome do arquivo do itemspec; caso contrário, corresponde com o itemspec inteiro. O valor padrão é `true`.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)