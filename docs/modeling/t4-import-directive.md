---
title: T4 Diretiva Import | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 5d581e182b39ac5a786b2d66a1a3798ba7fe82ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="t4-import-directive"></a>Diretiva de importação T4
Em blocos de código de um modelo de texto T4 do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a diretiva `import` permite que você referencie os elementos em outro namespace sem fornecer um nome totalmente qualificado. É o equivalente de `using` em C# ou `imports` em [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Para obter uma visão geral de escrever modelos de texto T4, consulte [gravando um modelo de texto T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-import-directive"></a>Usando a diretiva de importação  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 Neste exemplo, o código do modelo pode omitir um namespace explícito para membros de System.IO:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## <a name="standard-imports"></a>Importações padrão  
 O seguinte namespace é importado automaticamente, para que não seja necessário gravar uma diretiva de importação para ele:  
  
-   `System`  
  
 Além disso, se você usar uma diretiva personalizada, o processador de diretriz pode importar alguns namespaces automaticamente.  
  
 Por exemplo, se você gravar modelos para uma linguagem específica do domínio (DSL), você não precisa gravar diretivas de importação para os namespaces a seguir:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Namespace do DSL  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva de assembly T4](../modeling/t4-assembly-directive.md)