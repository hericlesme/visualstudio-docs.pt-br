---
title: Tarefa WriteCodeFragment | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d08d4499ba0fcdc044b7189abeb9de1716b7ba4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="writecodefragment-task"></a>Tarefa WriteCodeFragment
Gera um arquivo de código temporário do fragmento de código gerado especificado. Não exclui o arquivo.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `WriteCodeFragment`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AssemblyAttributes`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Descrição dos atributos para gravação. O item `Include` valor é o nome completo do tipo de atributo, por exemplo, "System.AssemblyVersionAttribute".<br /><br /> Cada metadados são o par nome-valor de um parâmetro, que deve ser do tipo `String`. Alguns atributos só permitem argumentos posicionais de construtor. No entanto, você pode usar esses argumentos em qualquer atributo. Para definir atributos de construtor posicional, use nomes de metadados que se assemelhem "_Parameter1", "_Parameter2" e assim por diante.<br /><br /> Um índice do parâmetro não pode ser ignorado.|  
|`Language`|Parâmetro `String` obrigatório.<br /><br /> Especifica a linguagem do código a ser gerado.<br /><br /> `Language` pode ser qualquer linguagem em que um provedor de CodeDom está disponível, por exemplo, "C#" ou "VisualBasic". O arquivo emitido terá a extensão de nome de arquivo padrão para esse idioma.|  
|`OutputDirectory`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica a pasta de destino para o código gerado, geralmente a pasta intermediária.|  
|`OutputFile`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o caminho do arquivo que foi gerado. Se esse parâmetro for definido usando um nome de arquivo, a pasta de destino será anexada ao nome do arquivo. Se for definido usando uma raiz, a pasta de destino será ignorada.<br /><br /> Se esse parâmetro não for definido, o nome do arquivo de saída será a pasta de destino, um nome de arquivo arbitrário e a extensão de nome de arquivo padrão para o idioma especificado.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)