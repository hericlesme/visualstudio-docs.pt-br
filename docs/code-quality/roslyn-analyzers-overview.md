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
ms.openlocfilehash: aaa989347744e015b90cca186c6aa9756dfe90fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Visão geral dos analisadores de plataforma de compilador do .NET

2017 do Visual Studio inclui um conjunto interno de analisadores de plataforma de compilador .NET que analisar seu código c# ou Visual Basic, conforme você digita. Você pode instalar analisadores adicionais como uma extensão do Visual Studio ou em uma base por projeto como um pacote do NuGet. Analisadores de examinar código estilo, a qualidade do código e facilidade de manutenção, design de código e outros problemas.

Se forem encontradas violações de regras por um analisador, são informados no editor de códigos como um *curvadas* sob o código incorreto e, no **lista de erros**.

Muitas regras do analisador, ou *diagnóstico*, ter uma ou mais associados *correções de código* que você pode aplicar para corrigir o problema. O diagnóstico de analisador que é integrado ao Visual Studio têm uma correção de código associado. Correções de código são mostradas no menu de ícone de lâmpada, juntamente com outros tipos de *ações rápidas*. Para obter informações sobre essas correções de código, consulte [ações rápidas comuns](../ide/common-quick-actions.md).

![Violação de analisador e correção de código de ação rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analisadores de Roslyn vs. de análise de código estático

Analisadores de plataforma de compilador .NET ("Roslyn") substituirá [análise de código estático](../code-quality/code-analysis-for-managed-code-overview.md) para código gerenciado. Muitas das regras de análise de código estático já foram reescritas como diagnóstico do Roslyn analisador.

Como violações de regras de análise de código estático, violações de analisador Roslyn aparecem no **lista de erros**. Além disso, violações de analisador Roslyn também aparecem no editor de códigos como *squigglies* sob o código incorreto. A cor do curvadas depende de [configuração de severidade](../code-quality/use-roslyn-analyzers.md#rule-severity) da regra. Captura de tela a seguir mostra três violações&mdash;um vermelho, um verde e um cinza:

![Squigglies no editor de códigos](media/diagnostics-severity-colors.png)

Analisadores de Roslyn analisar o código no momento da compilação, como análise de código estático se ele está habilitado, mas também em tempo real conforme você digita! Analisadores de Roslyn também podem fornecer análise em tempo de design dos arquivos de código que não estão abertos no editor, se você habilitar [completa de análise de solução](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Erros de tempo de compilação e avisos do Roslyn analisadores são mostrados apenas se os analisadores são instalados como um pacote do NuGet.

Não apenas Roslyn analisadores relatar os mesmos tipos de problemas que a análise de código estático, mas eles facilitam corrigir um ou todos, ocorrências da violação de no arquivo ou projeto. Essas ações são chamadas *correções de código*. Correções de código são específicos do IDE; no Visual Studio, eles são implementados como [ações rápidas](../ide/quick-actions.md). Nem todos os diagnósticos de analisador têm uma correção de código associado.

> [!NOTE]
> A opção de menu **analisar** > **executar análise de código** aplica-se a análise de código estático somente para. Além disso, em um projeto **análise de código** página de propriedade, o **habilitar análise de código no Build** e **Suprimir resultados do código gerado** caixas de seleção só se aplicam ao análise de código estático. Eles não têm efeito sobre os analisadores de Roslyn.

Para diferenciar as violações de analisadores de Roslyn e análise de código estático no **lista de erros**, examine o **ferramenta** coluna. Se o valor de ferramenta corresponde a um dos assemblies do analisador de **Solution Explorer**, por exemplo **Microsoft.CodeQuality.Analyzers**, a violação vêm de um analisador de Roslyn. Caso contrário, a violação se origina de análise de código estático.

![Coluna de ferramenta na lista de erros](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-vs-extension"></a>Pacote do NuGet versus extensão

Plataforma de compilador .NET analisadores podem ser instalado por projeto através de um pacote NuGet ou todo o Visual Studio como uma extensão do Visual Studio. Há algumas diferenças de comportamento das teclas entre esses dois métodos de [instalar analisadores de](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Escopo

Se você instalar analisadores como uma extensão do Visual Studio, eles se aplicam no nível da solução, a todas as instâncias do Visual Studio. Se você instalar os analisadores como um pacote do NuGet, que é o método preferencial, elas se aplicam somente ao projeto em que o pacote NuGet foi instalado. Em ambientes de equipe, analisadores instalados como pacotes NuGet estão no escopo para *todos os desenvolvedores* que trabalhar no projeto.

### <a name="build-errors"></a>Erros de compilação

Para que as regras aplicadas em tempo de compilação, inclusive por meio da linha de comando ou como parte de uma integração contínua (CI) compilação, instale os analisadores como um pacote do NuGet. Erros e avisos do analisador não aparecem no relatório de compilação se você instalar os analisadores como uma extensão.

Captura de tela a seguir mostra a saída da compilação de linha de comando de criação de um projeto que contém uma violação de regra do analisador:

![Saída de MSBuild com violação de regra](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravidade da regra

Você não pode definir a severidade das regras de analisadores que foram instaladas como uma extensão do Visual Studio. Para configurar [regra severidade](../code-quality/use-roslyn-analyzers.md#rule-severity), instale os analisadores como um pacote do NuGet.

## <a name="next-steps"></a>Próximas etapas

- [Instalar analisadores de Roslyn no Visual Studio](../code-quality/install-roslyn-analyzers.md)
- [Use os analisadores de Roslyn no Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Consulte também

- [Ações rápidas no Visual Studio](../ide/quick-actions.md)
- [Gravar seu próprio analisador Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK de plataforma de compilador do .NET](/dotnet/csharp/roslyn-sdk/)