---
title: Classe base Task | Microsoft Docs
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
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b2b269d718871c58cb082ce09ed50ce70736b55
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465398"
---
# <a name="task-base-class"></a>Classe base Task
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tarefa de classe Base](https://docs.microsoft.com/visualstudio/msbuild/task-base-class).  
  
  
Muitas tarefas são herdadas da classe <xref:Microsoft.Build.Utilities.Task>. Essa classe adiciona vários parâmetros para as tarefas que derivam dela. Esses parâmetros são listados neste documento.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros dessa classe base.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas. O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas retornem para ele.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas. O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas retornem para ele.<br /><br /> Esta é uma propriedade de conveniência para que os autores de tarefa que herdam desta classe não precisem converter o valor de `IBuildEngine` para `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível pelo host.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parâmetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica a instância do objeto de host (pode ser nulo). O mecanismo de compilação define essa propriedade se o IDE do host associou um objeto de host com essa tarefa em particular.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Parâmetro <xref:Microsoft.Build.Utilities.TaskLoggingHelper> somente leitura opcional.<br /><br /> O objeto auxiliar de registro em log.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)



