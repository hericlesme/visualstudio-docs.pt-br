---
title: Como usar caracteres XML reservados em arquivos de projeto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f045195a4e934fcb6e140da68528ca43f104136d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464115"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Como usar caracteres XML reservados em arquivos de projeto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: uso de caracteres XML reservados em arquivos de projeto](https://docs.microsoft.com/visualstudio/msbuild/how-to-use-reserved-xml-characters-in-project-files).  
  
  
Quando você cria arquivos de projeto, talvez seja necessário usar caracteres XML reservados, por exemplo, nos valores de propriedade ou em valores de parâmetro de tarefa. No entanto, alguns caracteres reservados devem ser substituídos por uma entidade nomeada para que o arquivo de projeto possa ser analisado.  
  
## <a name="using-reserved-characters"></a>Usando caracteres reservados  
 A tabela a seguir descreve os caracteres XML reservados que devem ser substituídos pela entidade nomeada correspondente para que o arquivo de projeto possa ser analisado.  
  
|Caractere reservado|Entidade nomeada|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Para usar aspas duplas em um arquivo de projeto  
  
-   Substitua as aspas duplas pela entidade nomeada correspondente, &quot;. Por exemplo, para colocar aspas duplas em torno da lista de itens `EXEFile`, digite:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Exemplo  
 No exemplo de código a seguir, as aspas duplas são usadas para realçar o nome de arquivo na mensagem gerada pelo arquivo de projeto.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência do MSBuild](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)


