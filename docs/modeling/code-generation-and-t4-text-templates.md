---
title: Geração de código e modelos de texto T4
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f4fed2cbf00717e4eaf9c1353370dbd96037491
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="code-generation-and-t4-text-templates"></a>Geração de código e modelos de texto T4

No Visual Studio, um *modelo de texto T4* é uma combinação de blocos de texto e lógica de controle que pode gerar um arquivo de texto. A lógica de controle é gravada como fragmentos de código de programa em [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. No Visual Studio 2015 atualização 2 e posterior, você pode usar os recursos da versão 6.0 c# em diretivas de modelos T4. O arquivo gerado pode ser texto de qualquer tipo, como uma página da Web, ou um arquivo de recurso ou o código-fonte programa em qualquer idioma.

Há dois tipos de modelos de texto T4: tempo de execução e tempo de design.

## <a name="run-time-t4-text-templates"></a>Modelos de texto T4 de tempo de execução

Também conhecido como 'pré-processados' modelos, modelos de tempo de execução são executados em seu aplicativo para gerar cadeias de caracteres de texto, normalmente como parte de sua saída. Por exemplo, você pode criar um modelo para definir uma página HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Observe que o modelo é semelhante a saída gerada. A similaridade do modelo para a saída resultante ajuda a evitar erros quando você deseja alterá-la.

Além disso, o modelo contém fragmentos de código do programa. Você pode usar esses fragmentos repetir seções de texto, para tornar as seções condicionais e para mostrar dados de seu aplicativo.

Para gerar a saída, o aplicativo chama uma função que é gerada pelo modelo. Por exemplo:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Seu aplicativo pode ser executado em um computador que não tenha instalado o Visual Studio.

Para criar um modelo de tempo de execução, adicione um **modelo de texto pré-processado** ao seu projeto. Como alternativa, você pode adicionar um arquivo de texto sem formatação e definir seu **ferramenta personalizada** propriedade **TextTemplatingFilePreprocessor**.

Para obter mais informações, consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Para obter mais informações sobre a sintaxe de modelos, consulte [gravando um modelo de texto T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Modelos de texto T4 tempo de design

Tempaltes de tempo de design definem a parte do código-fonte e outros recursos do seu aplicativo. Normalmente você usar vários modelos de leem os dados em um único arquivo de entrada ou o banco de dados e gerar alguns dos seus *. CS*, *. vb*, ou outros arquivos de origem. Cada modelo gera um arquivo. Elas são executadas no Visual Studio ou o MSBuild.

Por exemplo, os dados de entrada podem ser um arquivo XML de dados de configuração. Sempre que você editar o arquivo XML durante o desenvolvimento, os modelos de texto regenerar parte do código do aplicativo. Um dos modelos poderia se parecer com o exemplo a seguir:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

Dependendo dos valores no arquivo XML gerado *. CS* arquivo seria semelhante ao seguinte:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Como outro exemplo, a entrada pode ser um diagrama de fluxo de trabalho em uma atividade de negócios. Quando os usuários alterarem seu fluxo de trabalho de negócios, ou quando você começa a trabalhar com novos usuários que têm um fluxo de trabalho diferente, é fácil de gerar novamente o código de acordo com o novo modelo.

Modelos de tempo de design tornam mais rápido e mais confiável para alterar a configuração, quando os requisitos de alteração. Normalmente, a entrada é definida em termos de requisitos de negócios, como no exemplo de fluxo de trabalho. Isso torna mais fácil discutir as alterações com os usuários. Modelos de tempo de design, portanto, são uma ferramenta útil em um processo de desenvolvimento ágil.

Para criar um modelo de tempo de design, adicione um **modelo de texto** ao seu projeto. Como alternativa, você pode adicionar um arquivo de texto sem formatação e definir seu **ferramenta personalizada** propriedade **TextTemplatingFileGenerator**.

Para obter mais informações, consulte [geração de código de tempo de Design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Para obter mais informações sobre a sintaxe de modelos, consulte [gravando um modelo de texto T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> O termo *modelo* , às vezes, é usado para descrever dados lidos por um ou mais modelos. O modelo pode estar em qualquer formato, em qualquer tipo de arquivo ou banco de dados. Ele não precisa ser um modelo UML ou um modelo de linguagem específica de domínio. 'Model' indica apenas que os dados podem ser definidos em termos de conceitos de negócios, em vez de que se assemelha o código.

O recurso de transformação de modelo de texto chamado *T4*.

## <a name="see-also"></a>Consulte também

- [Gerar código com base em uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)