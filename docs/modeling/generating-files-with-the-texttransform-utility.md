---
title: Gerando arquivos com o utilitário TextTransform no Visual Studio | Microsoft Docs
ms.date: 03/22/2018
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5ecc5af3c37889bc79dc5978c33caf8249433978
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="generate-files-with-the-texttransform-utility"></a>Gerar arquivos com o utilitário TextTransform

TextTransform.exe é uma ferramenta de linha de comando que você pode usar para transformar um modelo de texto. Ao chamar TextTransform.exe, você especifica o nome de um arquivo de modelo de texto como um argumento. TextTransform.exe chama o mecanismo de transformação de texto e processa o modelo de texto. TextTransform.exe geralmente é chamado de scripts. No entanto, não é geralmente necessário, porque você pode executar a transformação de texto no Visual Studio ou no processo de compilação.

> [!NOTE]
> Se você deseja executar a transformação de texto como parte de um processo de compilação, considere usar a tarefa de transformação de texto do MSBuild. Para obter mais informações, consulte [geração de código em um processo de compilação](../modeling/code-generation-in-a-build-process.md). Em uma máquina na qual [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estiver instalado, você também pode escrever um aplicativo ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão que pode transformar modelos de texto. Para obter mais informações, consulte [processar modelos de texto usando um Host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe está localizado no seguinte diretório:

 **\Program arquivos (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

para a edição Professional, ou

 **\Program arquivos (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 para o Enterprise edition.

Nas versões anteriores do Visual Studio, o arquivo está localizado no seguinte local:

**\Program arquivos (x86) \Common Files\Microsoft Shared\TextTemplating\{versão}**

onde {version} depende de qual versão anterior está instalada.

## <a name="syntax"></a>Sintaxe

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parâmetros

|**Argumento**|**Descrição**|
|------------------|---------------------|
|`templateName`|Identifica o nome do arquivo de modelo que você deseja transformar.|

|**Opção**|**Descrição**|
|----------------|---------------------|
|**-out** \<filename>|O arquivo para o qual a saída da transformação é gravada.|
|**-r** \<assembly>|Um assembly usado para compilar e executar o modelo de texto.|
|**-u** \<namespace>|Um namespace que é usado para compilar o modelo.|
|**-I** \<includedirectory >|Um diretório que contém os modelos de texto incluídos no modelo de texto especificado.|
|**-P** \<referencepath >|Um diretório para procurar por assemblies especificados no modelo de texto ou usando o **- r** opção.<br /><br /> Por exemplo, para incluir os assemblies usados para a API do Visual Studio, use<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|O nome, o nome completo do tipo e o assembly de um processador de diretiva que pode ser usado para processar diretivas personalizadas dentro do modelo de texto.|
|**-a** [processorName]![directiveName]!\<parameterName>!\<parameterValue>|Especifique um valor de parâmetro para um processador de diretiva. Se você especificar apenas o nome do parâmetro e valor, o parâmetro estará disponível para todos os processadores de diretiva. Se você especificar um processador de diretiva, o parâmetro está disponível somente para o processador especificado. Se você especificar um nome de diretiva, o parâmetro está disponível apenas quando a diretiva especificada está sendo processada.<br /><br /> Para acessar os valores de parâmetro de um processador de diretiva ou o modelo de texto, use [ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx). Em um modelo de texto incluem `hostspecific` na diretiva de modelo e invocar a mensagem em `this.Host`. Por exemplo:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Sempre digite o '!' marca, mesmo se você omitir os nomes de diretiva e de processador opcional. Por exemplo:<br /><br /> `-a !!param!value`|
|**-h**|Fornece ajuda.|

## <a name="related-topics"></a>Tópicos relacionados

|Tarefa|Tópico|
|----------|-----------|
|Gerar arquivos em uma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Geração de código no tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Grave processadores de diretivas para transformar suas próprias fontes de dados.|[Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md)|
|Grave um host de modelagem de texto que permite que você chame os modelos de texto de seu próprio aplicativo.|[Processando modelos de texto usando um host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)|