---
title: Acessando o Visual Studio ou outros hosts a partir de um modelo de texto
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 657abba976e0f0d167651943289296d340981e62
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946511"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Acessar o Visual Studio ou outros Hosts de um modelo de texto

Em um modelo de texto, você pode usar os métodos e propriedades que são expostas pelo host que executa o modelo. O Visual Studio é um exemplo de um host.

> [!NOTE]
> Você pode usar propriedades e métodos de host em modelos de texto normal, mas não em *pré-processados* modelos de texto.

## <a name="obtain-access-to-the-host"></a>Obter acesso ao host

Para acessar o host, defina `hostspecific="true"` no `template` diretiva. Agora você pode usar `this.Host`, que tem o tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. O <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> tipo tem membros que você pode usar, por exemplo, para resolver nomes de arquivo e registro de erros.

### <a name="resolve-file-names"></a>Resolver nomes de arquivo

Para localizar o caminho completo de um arquivo relativo para o modelo de texto, use `this.Host.ResolvePath()`.

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

### <a name="display-error-messages"></a>Exibir mensagens de erro

Este exemplo registra mensagens quando você transforma o modelo. Se o host for Visual Studio, os erros são adicionados para o **lista de erros**.

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

## <a name="use-the-visual-studio-api"></a>Use a API do Visual Studio

Se você estiver executando um modelo de texto no Visual Studio, você pode usar `this.Host` para acessar os serviços fornecidos pelo Visual Studio e quaisquer pacotes ou as extensões que são carregadas.

Definir hostspecific = "true" e converter `this.Host` para <xref:System.IServiceProvider>.

Este exemplo obtém a API do Visual Studio, <xref:EnvDTE.DTE>, como um serviço:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Usar hostSpecific com herança do modelo

Especifique `hostspecific="trueFromBase"` se você usar também o `inherits` atributo, e se você herdar de um modelo que especifica `hostspecific="true"`. Se você não fizer isso, você pode obter um compilador avisando que a propriedade `Host` declarou duas vezes.