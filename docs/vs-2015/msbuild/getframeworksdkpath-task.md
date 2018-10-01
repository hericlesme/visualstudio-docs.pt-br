---
title: Tarefa GetFrameworkSdkPath | Microsoft Docs
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
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3e35cac8399ab97ae3825e35de5b249db7e23a7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460702"
---
# <a name="getframeworksdkpath-task"></a>Tarefa GetFrameworkSdkPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tarefa GetFrameworkSdkPath](https://docs.microsoft.com/visualstudio/msbuild/getframeworksdkpath-task).  
  
  
Recupera o caminho para o [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `GetFrameworkSdkPath`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o caminho para o SDK do .NET versão 2.0, se presente. Caso contrário, retornará `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o caminho para o SDK do .NET versão 3.5, se presente. Caso contrário, retornará `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o caminho para o SDK do .NET versão 4.0, se presente. Caso contrário, retornará `String.Empty`.|  
|`Path`|Parâmetro de saída `String` opcional.<br /><br /> Contém o caminho para o SDK mais recente do .NET, se houver qualquer versão. Caso contrário, retornará `String.Empty`.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `GetFrameworkSdkPath` para armazenar o caminho para o [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] na propriedade `SdkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)



