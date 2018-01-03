---
title: Tarefa XslTransformation | Microsoft Docs
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
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac5070e874551aea3880428b106ccb13c7c76c4c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xsltransformation-task"></a>Tarefa XslTransformation
Transformações um XML de entrada usando um XSLT ou XSLT compilado e saídas para um arquivo ou um dispositivo de saída.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `XslTransformation`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`OutputPaths`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos de saída para a transformação XML.|  
|`Parameters`|Parâmetro `String` opcional.<br /><br /> Especifica os parâmetros para o documento de entrada XSLT.|  
|`XmlContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XML como uma cadeia de caracteres.|  
|`XmlInputPaths`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos de entrada XML.|  
|`XslCompiledDllPath`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o XSLT compilado.|  
|`XslContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XSLT como uma cadeia de caracteres.|  
|`XslInputPath`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o arquivo de entrada XSLT.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)