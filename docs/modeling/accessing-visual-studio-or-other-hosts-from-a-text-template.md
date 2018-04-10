---
title: Acessando o Visual Studio ou outros Hosts de um modelo de texto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: cd72a2838e9dd7a903e5cf76aac30e2922708872
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Acessando o Visual Studio ou outros hosts a partir de um modelo de texto
Em um modelo de texto, você pode usar os métodos e propriedades expostos pelo host que executa o modelo, como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Isso se aplica a modelos de texto normal, modelos de texto não pré-processados.  
  
## <a name="obtaining-access-to-the-host"></a>Como obter acesso ao host  
 Definir `hostspecific="true"` no `template` diretiva. Isso permite que você use `this.Host`, que tem o tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Esse tipo tem membros que você pode usar, por exemplo, para resolver nomes de arquivo e registro de erros.  
  
### <a name="resolving-file-names"></a>Resolução de nomes de arquivo  
 Para localizar o caminho completo de um arquivo relativo para o modelo de texto, use isso. Host.ResolvePath().  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.IO" #>  
<#  
 // Find a path within the same project as the text template:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
### <a name="displaying-error-messages"></a>Exibindo mensagens de erro  
 Este exemplo registra mensagens quando você transforma o modelo. Se o host for [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], eles são adicionados à janela de erro.  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.CodeDom.Compiler" #>  
<#  
  string message = "test message";  
  this.Host.LogErrors(new CompilerErrorCollection()   
    { new CompilerError(  
       this.Host.TemplateFile, // Identify the source of the error.  
       0, 0, "0",   // Line, column, error ID.  
       message) }); // Message displayed in error window.  
#>  
  
```  
  
## <a name="using-the-visual-studio-api"></a>Usando a API do Visual Studio  
 Se você estiver executando um modelo de texto em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode usar `this.Host` para acessar os serviços fornecidos pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e quaisquer pacotes ou as extensões que são carregadas.  
  
 Definir hostspecific = "true" e converter `this.Host` para <xref:System.IServiceProvider>.  
  
 Este exemplo obtém o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API, <xref:EnvDTE.DTE>, como um serviço:  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#   
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
```  
  
## <a name="using-hostspecific-with-template-inheritance"></a>Usando hostSpecific com herança de modelo  
 Especifique `hostspecific="trueFromBase"` se você usar também o `inherits` atributo, e se você herdar de um modelo que especifica `hostspecific="true"`. Isso evita que um aviso do compilador para o efeito que a propriedade `Host` declarou duas vezes.