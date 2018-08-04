---
title: Analisadores de Roslyn no Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3d5836c0522ef97a634f44799934aab2750b3a45
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511416"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Visão geral dos analisadores do .NET Compiler Platform

Visual Studio 2017 inclui um conjunto interno de analisadores do .NET Compiler Platform que analisam seu código c# ou Visual Basic, conforme você digita. Você pode instalar outros analisadores como uma extensão do Visual Studio, ou em uma base por projeto como um pacote do NuGet. Analisadores de examinam o estilo de código, a qualidade do código e facilidade de manutenção, design de código e outros problemas.

Se violações de regra são encontradas por um analisador, são relatadas no editor de código como um *ondulada* sob o código incorreto e, na **lista de erros**.

Muitas regras do analisador, ou *diagnósticos*, tem uma ou mais associados *correções de código* que você pode aplicar para corrigir o problema. O analisador de diagnóstico que é criado no Visual Studio tem uma correção de código associado. Correções de código são mostradas no menu do ícone de lâmpada, juntamente com outros tipos de *ações rápidas*. Para obter informações sobre essas correções de código, consulte [ações rápidas comuns](../ide/common-quick-actions.md).

![Violação de analisador e correção de código de ação rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analisadores de Roslyn versus a análise de código estático

Analisadores do .NET compiler Platform ("Roslyn") substituirá [análise de código estático](../code-quality/code-analysis-for-managed-code-overview.md) para código gerenciado. Muitas das regras de análise estática de código já foram reescritas como diagnósticos de analisador Roslyn.

Como violações de regra de análise de código estático, violações de analisador Roslyn aparecem na **Error List**. Além disso, as violações de analisador Roslyn também são mostrados no editor de códigos, como *squigglies* sob o código incorreto. A cor do ondulada depende de [configuração de gravidade](../code-quality/use-roslyn-analyzers.md#rule-severity) da regra. Captura de tela a seguir mostra três violações&mdash;um vermelho, um verde e um cinza:

![Squigglies no editor de códigos](media/diagnostics-severity-colors.png)

Analisadores de Roslyn analisar o código no momento da compilação, como análise de código estático se estiver habilitado, mas também em tempo real conforme você digita! Analisadores de Roslyn também podem fornecer a análise de tempo de design dos arquivos de código que não estão abertos no editor, se você habilitar [análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Erros de tempo de compilação e avisos de analisadores de Roslyn são mostrados apenas se os analisadores são instalados como um pacote do NuGet.

Não apenas fazer analisadores Roslyn relatar os mesmos tipos de problemas que faz a análise de código estático, mas eles facilitam corrigir uma ou todas as ocorrências da violação em seu arquivo ou projeto. Essas ações são denominadas *correções de código*. Correções de código são específicas do IDE; no Visual Studio, eles são implementados como [ações rápidas](../ide/quick-actions.md). Nem todos os diagnósticos do analisador de tem uma correção de código associado.

> [!NOTE]
> A opção de menu **Analyze** > **executar análise de código** aplica-se a análise de código apenas como estático. Além disso, em um projeto **análise de código** página de propriedade, o **habilitar análise de código no Build** e **Suprimir resultados do código gerado** caixas de seleção só se aplicam aos análise de código estático. Eles não têm efeito sobre os analisadores do Roslyn.

Para diferenciar entre as violações de analisadores de Roslyn e análise de código estático na **lista de erros**, examine o **ferramenta** coluna. Se o valor de ferramenta corresponde a um dos assemblies no analisador **Gerenciador de soluções**, por exemplo **Microsoft.CodeQuality.Analyzers**, a violação vem de um analisador Roslyn. Caso contrário, a violação proveniente de análise de código estático.

![Coluna de ferramenta na lista de erros](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>Pacote do NuGet em comparação com a extensão do VSIX

.NET compiler Platform analisadores podem ser instalados por projeto por meio de um pacote do NuGet ou todo o Visual Studio como uma extensão do Visual Studio. Há algumas diferenças de comportamento da tecla entre esses dois métodos de [instalar analisadores](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Escopo

Se você instalar analisadores como uma extensão do Visual Studio, eles se aplicam no nível da solução, a todas as instâncias do Visual Studio. Se você instalar os analisadores como um pacote do NuGet, que é o método preferencial, elas se aplicam apenas ao projeto em que o pacote do NuGet foi instalado. Em ambientes de equipe, analisadores instalados como pacotes NuGet estão no escopo para *todos os desenvolvedores* que trabalham em que o projeto.

### <a name="build-errors"></a>Erros de compilação

Para que as regras de imposto no momento da compilação, incluindo por meio da linha de comando ou como parte de uma integração contínua (CI) build, instale os analisadores como um pacote do NuGet. Erros e avisos do analisador não aparecem no relatório de compilação se você instalar os analisadores como uma extensão.

Captura de tela a seguir mostra a saída de compilação de linha de comando desde a criação de um projeto que contém uma violação de regra do analisador:

![Saída do MSBuild com violação de regra](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravidade da regra

Você não pode definir a severidade das regras de analisadores que foram instalados como uma extensão do Visual Studio. Para configurar [severidade da regra](../code-quality/use-roslyn-analyzers.md#rule-severity), instalar os analisadores como um pacote do NuGet.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Instalar analisadores de Roslyn no Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usar os analisadores de Roslyn no Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Consulte também

- [Ações rápidas no Visual Studio](../ide/quick-actions.md)
- [Escrever seu próprio analisador Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK do .NET compiler Platform](/dotnet/csharp/roslyn-sdk/)