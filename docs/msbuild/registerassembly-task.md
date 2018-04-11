---
title: Tarefa RegisterAssembly | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9d4d1f5cda41fd7c72d32feda40f62d691a0d3cd
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="registerassembly-task"></a>Tarefa RegisterAssembly
Lê os metadados dentro do assembly especificado e adiciona as entradas necessárias ao Registro, que permite que clientes COM criem classes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de maneira transparente. O comportamento dessa tarefa é semelhante, mas não idêntico ao do [Regasm.exe (ferramenta de registro de Assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `RegisterAssembly`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Assemblies`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os assemblies a serem registrados com COM.|  
|`AssemblyListFile`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Contém informações sobre o estado entre a tarefa `RegisterAssembly` e a tarefa [UnregisterAssembly](../msbuild/unregisterassembly-task.md). Isso impede que a tarefa `UnregisterAssembly` da tentativa de cancelar o registro de um assembly que falhou ao se registrar na tarefa `RegisterAssembly`.|  
|`CreateCodeBase`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, cria uma entrada Codebase no Registro, que especifica o caminho de arquivo de um assembly não instalado no cache de assembly global. Você não deverá especificar essa opção se você instalar subsequentemente o assembly que está registrando no cache de assembly global.|  
|`TypeLibFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica a biblioteca de tipos a ser gerada do assembly especificado. A biblioteca de tipos gerada contém definições dos tipos acessíveis definidos no assembly. A biblioteca de tipos será gerada apenas se uma das seguintes opções for verdadeira:<br /><br /> – Uma biblioteca de tipos com esse nome não existe nesse local.<br />–  Uma biblioteca de tipos existe, mas é mais antiga que o assembly que está sendo passado.<br /><br /> Se a biblioteca de tipos for mais recente do que o assembly sendo passado, uma nova biblioteca não será criada, mas ainda assim o assembly será registrado.<br /><br /> Se esse parâmetro for especificado, ele deverá ter o mesmo número de itens que o parâmetro `Assemblies` ou a tarefa falhará. Se nenhuma entrada for especificada, a tarefa assumirá por padrão o nome do assembly e alterará a extensão do item para .tlb.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `RegisterAssembly` para registrar o assembly especificado pela coleção de itens `MyAssemblies`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)