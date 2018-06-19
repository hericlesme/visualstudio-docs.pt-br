---
title: Tarefa VCMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8ef67a4fa19bd715e73e50fcc268aee7a4df5d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31574517"
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