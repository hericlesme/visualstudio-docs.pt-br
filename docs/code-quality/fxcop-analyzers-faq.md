---
title: Análise de código FxCop e analisadores FxCop
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136362"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Perguntas frequentes sobre o FxCop e o FxCop analisadores

Pode ser um pouco confuso entender as diferenças entre o FxCop herdado e o FxCop analisadores. Este artigo visa para abordar algumas das perguntas que você pode ter.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Qual é a diferença entre o FxCop herdado e o FxCop analisadores?

FxCop herdado executa a análise de pós-compilação em um assembly compilado. Ele é executado como um executável separado chamado **FxCopCmd.exe**. FxCopCmd.exe carrega o assembly compilado, executa a análise de código e, em seguida, relata os resultados (ou *diagnóstico*).

Analisadores FxCop baseiam-se na plataforma do compilador .NET ("Roslyn"). Você [instalá-los como um pacote do NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) que é referenciado pelo projeto ou solução. Analisadores FxCop executados o código-fonte com base em análise durante a execução do compilador. Analisadores FxCop são hospedados dentro do processo de compilador, tanto **csc.exe** ou **vbc.exe**, e executar a análise quando o projeto é compilado. Resultados do analisador são relatados, juntamente com os resultados do compilador.

> [!NOTE]
> Você também pode [instalar analisadores FxCop como uma extensão do Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). Nesse caso, os analisadores execute conforme você digita no editor de código, mas eles não executados no momento da compilação. Se você quiser executar analisadores FxCop como parte da integração contínua (CI), instalá-los como um pacote do NuGet em vez disso.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>O comando Executar análise de código executar analisadores FxCop?

Nº Quando você seleciona **Analyze** > **executar análise de código** no Visual Studio 2017, ele executa análise de código estático ou FxCop herdado. **Executar análise de código** não tem efeito sobre os analisadores do roslyn, incluindo os analisadores FxCop baseada em Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>A propriedade de projeto do msbuild {1&gt;runcodeanalysis&lt;1 executar analisadores?

Nº O **{1&gt;runcodeanalysis&lt;1** propriedade em um arquivo de projeto (por exemplo, *csproj*) só é usado para executar o FxCop herdado. Ele executa uma tarefa de msbuild pós-compilação que invoca **FxCopCmd.exe**. Isso é equivalente a selecionar **Analyze** > **executar análise de código** no Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Então, como executar analisadores FxCop, em seguida?

Para executar os analisadores FxCop, primeiro [instalar o pacote NuGet](install-fxcop-analyzers.md) para eles. Em seguida, crie seu projeto ou solução do Visual Studio ou usando o msbuild. Os avisos e erros que geram os analisadores FxCop aparecerá na **Error List** ou a janela de comando.

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores do .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Introdução ao analisadores](fxcop-analyzers.yml)
- [Instalar analisadores FxCop](install-fxcop-analyzers.md)
