---
title: Processando modelos de texto usando um host personalizado
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: def1e625df1760728ef71a926671a3c4c4ccbf40
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Modelos de processo de texto usando um Host personalizado

O *transformação de modelo de texto* processo leva um *modelo de texto* arquivo como entrada e produz um arquivo de texto como a saída. Você pode chamar o mecanismo de transformação de texto de uma extensão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou da execução do aplicativo autônomo em um computador em que o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está instalado. No entanto, você deve fornecer um *host de modelagem de texto*. Essa classe conecta o modelo ao ambiente, localizando recursos, como assemblies e arquivos de inclusão, e resolvendo a saída e as mensagens de erro.

> [!TIP]
> Se você estiver escrevendo um pacote ou uma extensão que executará dentro do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], considere usar o serviço de modelagem de texto, em vez de escrever seu próprio host. Para obter mais informações, consulte [invocando transformação de texto em uma extensão VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Não recomendamos usar transformações de modelo de texto em aplicativos de servidor. Não recomendamos usar transformações de modelo de texto, exceto em um thread único. Isso ocorre porque o mecanismo de modelagem de texto reutiliza um único AppDomain para converter, compilar e executar modelos. O código convertido não foi criado para ser isento de threads. O mecanismo é criado para processar arquivos em série, pois estão em um projeto do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no tempo de design.
>
> Para aplicativos de tempo de execução, considere o uso de modelos de texto pré-processados: consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Se seu aplicativo usa um conjunto de modelos que são fixos no tempo de compilação, é mais fácil usar modelos de texto pré-processados. Você também pode usar essa abordagem se seu aplicativo for executado em um computador em que o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não está instalado. Para obter mais informações, consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Executar um modelo de texto em seu aplicativo

Para executar um modelo de texto, chame o método ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Seu aplicativo deve localizar e fornecer o modelo, e deve lidar com a saída.

 No parâmetro `host`, você deve fornecer uma classe que implementa <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Isso é chamado novamente pelo mecanismo.

 O host deve ser capaz de registrar erros, resolver referências ao assembly e arquivos de inclusão, fornecer um domínio de aplicativo no qual o modelo pode executar e chamar o processador adequado para cada diretiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> é definido em **Microsoft.VisualStudio.TextTemplating.\*. 0. dll**, e <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> é definido em **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0. dll de**.

## <a name="in-this-section"></a>Nesta seção
 [Passo a passo: Criando um Host de modelo de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md) mostra como criar um host de modelo de texto personalizado que faz parte externa do texto modelo funcionalidade disponível [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="reference"></a>Referência
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>Seções relacionadas

- [O processo de transformação de modelo de texto](../modeling/the-text-template-transformation-process.md) descreve o funcionamento de transformação de texto, e quais partes que você podem personalizar.
- [Criando processadores de diretiva de modelo do personalizado T4 texto](../modeling/creating-custom-t4-text-template-directive-processors.md) fornece uma visão geral do texto processadores de diretiva de modelo.