---
title: Instalar analisadores de Roslyn no Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8a3b40b3b471e6bb57da561ac51f23086a0f01bd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="install-net-compiler-platform-analyzers"></a>Instalar analisadores de plataforma de compilador do .NET

2017 do Visual Studio inclui um conjunto principal de plataforma de compilador .NET (*Roslyn*) analisadores. Esses analisadores estão sempre ativados. Você pode instalar analisadores adicionais, como pacotes do NuGet ou como extensões do Visual Studio em *VSIX* arquivos.

## <a name="to-install-nuget-package-analyzers"></a>Para instalar analisadores de pacote do NuGet

1. [Determinar qual versão do pacote de analisador](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages) para instalar, com base na sua versão do Visual Studio.

1. Instalar o pacote no Visual Studio, usando o [Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou [Package Manager UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > A página nuget.org para cada pacote de analisador mostra o comando para colar o **Package Manager Console**. Ainda há um botão útil para copiar o texto na área de transferência.
   >
   > ![Página NuGet.org mostrando o comando do Console do Gerenciador de pacotes](media/nuget-package-manager-command.png)

   Os assemblies do analisador estão instalados e aparecem em **Solution Explorer** em **referências** > **analisadores**.

   ![Nó de analisadores no Gerenciador de soluções](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>Para instalar analisadores VSIX

1. No Visual Studio, selecione **ferramentas** > **extensões e atualizações**.

   A caixa de diálogo **Extensões e Atualizações** é aberta.

   > [!NOTE]
   > Como alternativa, baixe a extensão diretamente do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Expanda **Online** no painel esquerdo e, em seguida, selecione **Visual Studio Marketplace**.

1. Na caixa de pesquisa, digite "análise de código" e procure o **2017 de análise de código Microsoft** extensão.

   ![Extensão de análise de código da Microsoft](media/extensions-and-updates-code-analysis.png)

1. Selecione **baixar**.

   A extensão é baixada.

1. Selecione **Okey** para fechar a caixa de diálogo e, em seguida, feche todas as instâncias do Visual Studio para iniciar o **instalador VSIX**.

   O **instalador VSIX** caixa de diálogo é aberta.

   ![Instalador do VSIX para análise de código da Microsoft](media/vsix-installer-code-analysis.png)

1. Selecione **modificar** para iniciar a instalação.

1. Depois de um ou dois minutos, a instalação for concluída. Selecione **fechar**.

1. Abra novamente o Visual Studio.

Se você deseja verificar se a extensão estiver instalado, selecione **ferramentas** > **extensões e atualizações**. No **extensões e atualizações** caixa de diálogo, selecione o **instalado** categoria à esquerda e, em seguida, procure a extensão pelo nome.

## <a name="next-steps"></a>Próximas etapas

- [Use os analisadores de Roslyn no Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores de Roslyn no Visual Studio](../code-quality/roslyn-analyzers-overview.md)