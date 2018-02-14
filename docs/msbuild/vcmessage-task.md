---
title: Tarefa VCMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8f3ec9c3b41d7ef8bffaa1dd1c607cd39610143b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="vcmessage-task"></a>Tarefa VCMessage
Registra mensagens de aviso e erro durante o build.  
  
## <a name="remarks"></a>Comentários  
 Essa tarefa ajuda a implementar o MSBuild para o Visual C++ e não se destina a ser chamada pelo usuário. Para obter mais informações, consulte <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **VCMessage**.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|**Argumentos**|Parâmetro **String** opcional.<br /><br /> Uma lista delimitada por ponto e vírgula de mensagens a serem exibidas.|  
|**Código**|Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Um número de erro que qualifica a mensagem.|  
|**Tipo**|Parâmetro **String** opcional.<br /><br /> Especifica o tipo de mensagem a ser emitida. Especifique `"Warning"` para emitir uma mensagem de aviso ou `"Error"` para emitir uma mensagem de erro.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)