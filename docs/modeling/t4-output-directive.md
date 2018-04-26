---
title: T4 Diretiva de saída
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6044dd970029b3f233f8b20eb2e334b5041ceb33
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="t4-output-directive"></a>T4 Diretiva de saída

Em modelos de texto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a diretiva de `output` é usada pare definir a extensão do nome de arquivo e a codificação do arquivo transformado.

 Por exemplo, se seu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto inclui um arquivo de modelo chamado **MyTemplate.tt** que contém a seguinte diretiva:

 `<#@output extension=".cs"#>`

 em seguida, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] irá gerar um arquivo chamado **MyTemplate.cs**

 A diretiva de `output` não é necessária em um modelo de texto de tempo de execução (pré-processado). Ao invés disso, o aplicativo obtém a cadeia de caracteres gerada ao chamar `TextTransform()`. Para obter mais informações, consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Usando a Diretiva de Saída

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Não deverá haver mais de uma diretiva de `output` em cada modelo de texto.

## <a name="extension-attribute"></a>atributo de extensão
 Especifica a extensão do nome de arquivo do arquivo de saída do texto gerado.

 O valor padrão é **. cs**

 Exemplos: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Os valores aceitáveis: Qualquer nome extensão de arquivo válida.

## <a name="encoding-attribute"></a>atributo de codificação
 Especifica a codificação usada ao gerar o arquivo de saída. Por exemplo:

 `<#@ output encoding="utf-8"#>`

 O valor padrão é a codificação usada pelo arquivo de modelo de texto.

 Valores aceitáveis: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Padrão do sistema)

 Em geral, é possível usar a cadeia de caracteres do WebName ou o número da CodePage de qualquer uma das codificações retornadas por <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.