---
title: Tarefa de mensagem | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7993fe70c52cfd0694bd50d873425eda82c0a7c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460724"
---
# <a name="message-task"></a>Tarefa Message
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tarefa Message](https://docs.microsoft.com/visualstudio/msbuild/message-task).  
  
  
Registra uma mensagem durante a compilação.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `Message`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Importance`|Parâmetro `String` opcional.<br /><br /> Especifica a importância da mensagem. Esse parâmetro pode ter um valor igual a `high`, `normal` ou `low`. O valor padrão é `normal`.|  
|`Text`|Parâmetro `String` opcional.<br /><br /> O texto de erro do log.|  
  
## <a name="remarks"></a>Comentários  
 A tarefa `Message` permite o envio de mensagens de problema para os agentes de log em diferentes etapas no processo de compilação de projetos [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Se o parâmetro `Condition` avaliar para o `true`, o valor do parâmetro `Text` será registrado e a compilação dará continuidade à execução. Se um parâmetro `Condition` não existir, o texto da mensagem será registrado. Para obter mais informações sobre registro, consulte [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Por padrão, a mensagem é enviada para o agente de log de console do MSBuild. Isso pode ser alterado configurando o parâmetro <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. O agente de log interpreta o parâmetro `Importance`.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir registra mensagens para todos os agentes de log registrados.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Obtendo Logs de Build](../msbuild/obtaining-build-logs-with-msbuild.md)



