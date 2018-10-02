---
title: Classe Base TaskExtension | Microsoft Docs
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
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc755abe558491eb1b4c6e0e9575b4a9b8d47884
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463457"
---
# <a name="taskextension-base-class"></a>Classe TaskExtension (base)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [classe de Base TaskExtension](https://docs.microsoft.com/visualstudio/msbuild/taskextension-base-class).  
  
  
Muitas tarefas são herdadas da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que é herdada da classe <xref:Microsoft.Build.Utilities.Task>. Esta cadeia de herança adiciona vários parâmetros nas tarefas que derivam deles. Esses parâmetros são listados neste documento.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros das classes base.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas. O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas retornem para ele.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas. O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas retornem para ele.<br /><br /> Esta é uma propriedade de conveniência para que os autores de tarefa que herdam desta classe não precisem converter o valor de `IBuildEngine` para `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível pelo host.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parâmetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica a instância do objeto de host (pode ser nulo). O mecanismo de compilação define essa propriedade se o IDE do host associou um objeto de host com essa tarefa em particular.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Parâmetro <xref:Microsoft.Build.Utilities.TaskLoggingHelper> somente leitura opcional.<br /><br /> Obtém um objeto `TaskLoggingHelperExtension` que contém os métodos de registro de tarefa.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)



