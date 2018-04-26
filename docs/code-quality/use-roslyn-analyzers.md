---
title: Usar e configurar os analisadores de Roslyn no Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2e99a98f5ea4cca5891d416bdc13656b3173a40f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Configurar e usar as regras do analisador Roslyn

Regras do analisador de plataforma de compilador .NET ("Roslyn"), ou *diagnóstico*, analisar seu código c# ou Visual Basic, conforme você digita. Cada diagnóstico tem um estado de gravidade e supressão de padrão que pode ser substituído para seu projeto. Este artigo aborda a severidade de regra de configuração, usando conjuntos de regras e suprimindo violações.

## <a name="analyzers-in-solution-explorer"></a>Analisadores no Gerenciador de soluções

Você pode fazer muito a personalização do diagnóstico do analisador de **Gerenciador de soluções**. Se você [instalar analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote do NuGet, um **analisadores** nó aparece no **referências** ou **dependências** nó  **Gerenciador de soluções**. Se você expandir **analisadores**e, em seguida, expanda um dos assemblies do analisador, você verá todos os diagnósticos no assembly.

![Nó de analisadores no Gerenciador de soluções](media/analyzers-expanded-in-solution-explorer.png)

Você pode exibir as propriedades de um diagnóstico, incluindo sua descrição e a severidade padrão, no **propriedades** janela. Para exibir as propriedades, clique na regra e selecione **propriedades**, ou selecione a regra e, em seguida, pressione **Alt**+**Enter**.

![Propriedades de diagnóstico na janela Propriedades](media/analyzer-diagnostic-properties.png)

Para ver a documentação online para obter um diagnóstico, clique com botão direito no diagnóstico e selecione **exibir ajuda**.

Os ícones ao lado de cada diagnóstico em **Solution Explorer** correspondem aos ícones que você vê no conjunto quando você abri-lo no editor de regras de:

- o "i" em um círculo indica um [severidade](#rule-severity) de **informações**
- o "!" em um triângulo indica um [severidade](#rule-severity) de **aviso**
- o "x" em um círculo indica um [severidade](#rule-severity) de **erro**
- o "i" em um círculo em um plano de fundo de cor clara indica um [severidade](#rule-severity) de **oculto**
- a seta apontando para baixo em um círculo indica que o diagnóstico é suprimido

![Ícones de diagnóstico no Gerenciador de soluções](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Conjuntos de regras

Um [conjunto de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) é um arquivo XML que armazena o estado de gravidade e supressão de diagnóstico individual. Conjuntos de regras se aplicam a um único projeto, e um projeto pode ter vários conjuntos de regras. Para exibir o conjunto no editor de regras ativo, clique duas vezes no **analisadores** nó **Solution Explorer** e selecione **abrir conjunto de regra de ativo**. Se isso for a primeira vez que você está acessando a regra definido, um arquivo chamado  *\<projectname >. RuleSet* é adicionado ao projeto e aparece no **Gerenciador de soluções**.

> [!NOTE]
> Conjuntos de regra incluem análise de código (binário) estático e regras do analisador de Roslyn.

Você pode alterar a regra active definidas para um projeto no **análise de código** guia de propriedades do projeto. Selecione o conjunto de regras de **executar esse conjunto de regras** lista suspensa. Você também pode abrir o conjunto de regras do **análise de código** página de propriedade selecionando **abrir**.

## <a name="rule-severity"></a>Gravidade da regra

Você pode configurar a severidade das regras do analisador, ou *diagnóstico*, se você [instalar os analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote do NuGet. A tabela a seguir mostra as opções de severidade de diagnóstico:

|Severidade|Comportamento de tempo de compilação|Comportamento do Editor|
|-|-|-|
|Erro|Violações aparecem como *erros* no **lista de erros** na linha de comando saída da compilação e causar compilações falha.|Código incorreto está sublinhado com um vermelho curvado e marcado por uma caixa vermelha pequena na barra de rolagem.|
|Aviso|Violações aparecem como *avisos* no **lista de erros** e na linha de comando saída da compilação, mas não causam compilações falha.|Código incorreto está sublinhado com uma verde curvada e marcada por uma caixa pequena verde na barra de rolagem.|
|Info|Violações aparecem como *mensagens* no **lista de erros**e não na saída da compilação de linha de comando.|Código incorreto está sublinhado com um cinza curvado e marcado por uma caixa pequena cinza na barra de rolagem.|
|Hidden|Não visíveis ao usuário.|Não visíveis ao usuário. O diagnóstico é relatado para o mecanismo de diagnóstico de IDE, no entanto.|
|Nenhum|Suprimida completamente.|Suprimida completamente.|

Além disso, você pode "Redefinir" gravidade da regra definindo-a como **padrão**. Cada diagnóstico com severidade padrão que pode ser vista no **propriedades** janela.

Captura de tela a seguir mostra três violações de diagnósticas diferentes no editor de códigos, com três severidades diferentes. Observe a cor do curvadas, bem como a caixa pequena na barra de rolagem à direita.

![Violação de informações, aviso e erro no editor de códigos](media/diagnostics-severity-colors.png)

Captura de tela a seguir mostra as violações de três mesmo que aparecem no **lista de erros**:

![Violação de erro, aviso e informações na lista de erros](media/diagnostics-severities-in-error-list.png)

Você pode alterar a severidade de uma regra de **Solution Explorer**, ou dentro de  *\<projectname >. RuleSet* arquivo que é adicionado à solução depois que você alterar a severidade de uma regra no  **Gerenciador de soluções**.

![Arquivo de conjunto de regras no Gerenciador de soluções](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Para definir a gravidade da regra no Gerenciador de soluções

1. Em **Solution Explorer**, expanda **referências** > **analisadores** (**dependências**  >  **Analisadores** para projetos do .NET Core).

1. Expanda o assembly que contém a regra que você deseja definir a severidade para.

1. Clique na regra e selecione **definir regra definir severidade**. No menu suspenso, selecione uma das opções de severidade.

   A gravidade da regra é salvo no arquivo de conjunto de regras ativo.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Definir regra de arquivo de conjunto de gravidade da regra

1. Abra o conjunto de regras arquivo clicando duas vezes no **Solution Explorer**, selecionando **abrir conjunto de regra de ativo** no menu de atalho do **analisadores** nó, ou selecionando **Abrir** no **análise de código** página de propriedades do projeto.

1. Navegue até a regra expandindo seu assembly que contém.

1. No **ação** coluna, selecione o valor para abrir uma lista suspensa e selecione a severidade desejada na lista.

   ![Abrir no editor do arquivo de conjunto de regras](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir violações

Há várias maneiras para suprimir as violações de regra:

- Para suprimir todas as violações atuais, selecione **analisar** > **executar análise de código e suprimir problemas ativos** na barra de menus. Isso às vezes é referenciado como "linha de base".

- Para suprimir um diagnóstico de **Solution Explorer**, defina sua severidade como **nenhum**.

- Para suprimir um diagnóstico do editor de conjunto de regras, desmarque a caixa ao lado de seu nome ou defina **ação** para **nenhum**.

- Para suprimir um diagnóstico de código no editor, posicione o cursor na linha de código com a violação e pressione **Ctrl**+**.** Para abrir o **ações rápidas** menu. Selecione **suprimir CAxxxx** > **na fonte** ou **suprimir CAxxxx** > **no arquivo de supressão**.

   ![Suprimir diagnóstico no menu Ações rápidas](media/suppress-diagnostic-from-editor.png)

- Para suprimir um diagnóstico do **lista de erros**, clique no erro, aviso ou mensagem e selecione **suprimir** > **na origem** ou **Suprimir** > **no arquivo de supressão**.

   - Se você selecionar **na origem**, o **visualizar alterações** caixa de diálogo é aberta e mostra uma visualização de C# [#pragma aviso](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) ou Visual Basic [#Disable aviso](/dotnet/visual-basic/language-reference/directives/directives) diretiva é adicionada ao código-fonte.

      ![Visualização de adicionar #pragma aviso no arquivo de código](media/pragma-warning-preview.png)

   - Se você selecionar **no arquivo de supressão**, o **visualizar alterações** caixa de diálogo é aberta e mostra uma visualização do <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo que é adicionado ao arquivo de supressões globais.

      ![Visualização de adicionar o atributo SuppressMessage ao arquivo de supressão](media/preview-changes-in-suppression-file.png)

   No **visualizar alterações** caixa de diálogo, selecione **aplicar**.

> [!NOTE]
> Em um projeto .NET Core, se você adicionar uma referência a um projeto que tem os analisadores de NuGet os analisadores são automaticamente adicionados ao projeto dependente muito. Para desabilitar esse comportamento, por exemplo, se o projeto dependente é um projeto de teste de unidade, marcar o pacote do NuGet como particular no *. csproj* ou *. vbproj* arquivo do projeto referenciado:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores de Roslyn no Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar um bug de analisador Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir avisos da análise de código](../code-quality/in-source-suppression-overview.md)