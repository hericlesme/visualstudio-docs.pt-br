---
title: Tarefa WriteLinesToFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 062270864c3fecb6556ef9b48d00177966a41859
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233016"
---
# <a name="writelinestofile-task"></a>Tarefa WriteLinesToFile
Grava os caminhos dos itens especificados no arquivo de texto especificado.  
  
## <a name="task-parameters"></a>Parâmetros de tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `WriteLinestoFile`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`File`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o arquivo no qual os itens serão gravados.|  
|`Lines`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os itens a serem gravados no arquivo.|  
|`Overwrite`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a tarefa substituirá todo o conteúdo existente no arquivo.|  
|`Encoding`|Parâmetro `String` opcional.<br /><br /> Seleciona a codificação de caracteres, por exemplo, "Unicode".  Confira também <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Comentários  
 Se `Overwrite` for `true`, criará um novo arquivo, gravará os conteúdos nele e o fechará. Se o arquivo de destino já existir, ele será substituído. Se `Overwrite` for `false`, acrescentará os conteúdos ao arquivo, criando um arquivo de destino, caso ele ainda não exista.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `WriteLinesToFile` para gravar os caminhos dos itens na coleção de itens `MyItems` no arquivo especificado pela coleção de itens `MyTextFile`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)