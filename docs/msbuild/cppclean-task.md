---
title: Tarefa CPPClean | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92ce404301b2eb2b631969db70fa1dce3febb72b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cppclean-task"></a>Tarefa CPPClean
Exclui os arquivos temporários criados pelo MSBuild quando projeto do Visual C++ é compilado. O processo de exclusão de arquivos de build é conhecido como *limpeza*.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **CPPClean**.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|**DeletedFiles**|Parâmetro de saída `ITaskItem[]` opcional.<br /><br /> Define uma matriz de itens de arquivo de saída do MSBuild que pode ser consumida e emitida por tarefas.|  
|**DoDelete**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, limpará arquivos de build temporários.|  
|**FilePatternsToDeleteOnClean**|Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de extensões de arquivo dos arquivos a serem limpos.|  
|**FilesExcludedFromClean**|Parâmetro `String` opcional.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de arquivos que não serão limpos.|  
|**FoldersToClean**|Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de diretórios a serem limpos. É possível especificar um caminho completo ou relativo e esse caminho pode conter o símbolo curinga (**\***).|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)