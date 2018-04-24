---
title: 'Início Rápido: análise de código para C/C++'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: e43c505716fe437f53ac1d1b8e7921ec76e153d0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="quickstart-code-analysis-for-cc"></a>Início rápido: Análise de código para C/C++

Você pode melhorar a qualidade do seu aplicativo ao executar análise de código regularmente em código C ou C++. Isso pode ajudá-lo a localizar problemas comuns de violações de práticas recomendadas de programação ou defeitos que são difíceis de descobrir com testes. Os avisos da análise de código diferem dos erros e avisos do compilador porque a análise de código procura por padrões de código específicos que são válidos, mas que ainda podem criar problemas para você ou outras pessoas que usam seu código.

## <a name="configure-rule-sets-for-a-project"></a>Configurar conjuntos de regras para um projeto

1. Em **Solution Explorer**, abra o menu de atalho para o nome do projeto e escolha **propriedades**.

2. As etapas a seguir são opcionais:

    1. No **configuração** e **plataforma** listas, escolha a plataforma de destino e a configuração de compilação.

    2. Por padrão, a análise de código não relata avisos de código que é gerado automaticamente por ferramentas externas. Para exibir avisos do código gerado, desmarque o **Suprimir resultados do código gerado** caixa de seleção.

        > [!NOTE]
        > Essa opção suprime erros de análise de código e avisos do código gerado quando os erros e avisos aparecem em formulários e modelos. Você pode exibir e manter o código-fonte para um formulário ou um modelo.

3. Para executar a análise de código toda vez que o projeto é compilado usando a configuração selecionada, selecione o **habilitar análise de código para C/C++ na compilação** caixa de seleção. Você também pode executar a análise de código manualmente abrindo o **analisar** menu e, em seguida, escolhendo **executar análise de código em** *ProjectName*.

4. No **executar esse conjunto de regras** lista, siga um destes procedimentos:

    - Escolha o conjunto de regras que você deseja usar.

    - Escolha  **\<procurar... >** para especificar uma regra personalizada existente de conjunto que não está na lista.

    - Definir um [conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Conjuntos de regras do C/C++ padrão

O Visual Studio inclui dois conjuntos de regras para código nativo padrão:

|Conjunto de regras|Descrição|
|--------------|-----------------|
|Regras recomendadas mínimas do Microsoft Native|Esse conjunto de regras enfoca os problemas mais críticos do código nativo, inclusive falhas potenciais de segurança e falhas de aplicativo. Você deve incluir este conjunto de regras em qualquer conjunto personalizado que criar para seus projetos nativos.|
|Regras nativas Microsoft recomendadas|Esse conjunto de regras abrange uma ampla gama de problemas. Ele inclui todas as regras no Microsoft nativo mínimo recomendado regras.|

## <a name="run-code-analysis"></a>Executar análise de código

Na página de análise de código das páginas de propriedades do projeto, você pode configurar a análise de código para executar cada vez que você compilar o projeto. Você também pode executar a análise de código manualmente.

Para executar análise de código em uma solução:

- No menu **Compilar**, escolha **Executar Análise de Código na Solução**.

 Para executar a análise de código em um projeto:

- No Gerenciador de soluções, escolha o nome do projeto.

- No **criar** menu, escolha **executar análise de código em** *nome do projeto*.

 O projeto ou solução é compilada e análise de código é executada. Os resultados aparecem na lista de erros.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analisar e resolver avisos da análise de código

Para analisar um aviso específico, escolha o título do aviso na lista de erros. O aviso se expande para exibir informações adicionais sobre o problema. Quando possível, análise de código exibe os números de linha e a lógica de análise que levou ao aviso. Para obter informações detalhadas sobre o aviso, incluindo as soluções possíveis para o problema, escolha a ID do aviso para exibir o tópico da Ajuda online correspondente.

Quando você seleciona um aviso, a linha de código que causaram o aviso é realçada no editor de código do Visual Studio.

Depois de entender o problema, você pode resolvê-lo no seu código. Em seguida, execute novamente a análise de código para certificar-se de que o aviso não aparece mais na lista de erros e se sua correção não gerou novos avisos.

## <a name="suppress-code-analysis-warnings"></a>Suprimir avisos da análise de código

Há ocasiões em que você pode decidir não corrigir um aviso de análise de código. Você pode decidir que resolver o aviso exige recodificação demais considerando a probabilidade de que o problema ocorrerá em qualquer implementação do seu código no mundo real. Ou você pode achar que a análise usada no aviso é inadequada nesse contexto específico. É possível suprimir avisos individuais para que eles não aparecem mais na lista de erros.

Para suprimir um aviso:

1. Se as informações detalhadas não for exibidas, escolha o título do aviso para expandi-lo.

2. Escolha o link **Ações** na parte inferior do aviso.

3. Escolha **suprimir mensagem** e, em seguida, escolha **na origem**.

 Suprimir uma mensagem insere `#pragma warning (disable:`*WarningId*`)`, que suprime o aviso para a linha de código.

## <a name="create-work-items-for-code-analysis-warnings"></a>Criar itens de trabalho para o código de avisos da análise

Você pode usar o recurso de rastreamento de item de trabalho para registrar bugs de dentro do Visual Studio. Para usar esse recurso, você deve se conectar a uma instância do Team Foundation Server.

**Para criar um item de trabalho para um ou mais avisos de código C/C++**

1. Na lista de erros, expanda e selecione os avisos

2. No menu de atalho para os avisos, escolha **Criar Item de trabalho**e, em seguida, escolha o tipo de item de trabalho.

3. Visual Studio cria um único item de trabalho para os avisos selecionados e exibe o item de trabalho em uma janela de documento do IDE.

4. Adicionar informações adicionais e, em seguida, escolha **Salvar Item de trabalho**.

## <a name="search-and-filter-code-analysis-results"></a>Pesquisar e filtrar os resultados da análise de código

Você pode pesquisar listas longas de mensagens de aviso e pode filtrar avisos em soluções multiprojeto.

- **Para filtrar avisos por título ou id de aviso**: insira a palavra-chave na caixa de pesquisa.

- **Para filtrar avisos por severidade**: por padrão, mensagens de análise de código são atribuídas a uma severidade de **aviso**. Você pode atribuir a severidade de uma ou mais mensagens como **erro** em uma regra personalizada definida. No **severidade** coluna o **lista de erros**, escolha a seta suspensa e, em seguida, no ícone de filtro. Escolha **aviso** ou **erro** para exibir apenas as mensagens que são atribuídas a severidade do respectiva. Escolha **Selecionar tudo** para exibir todas as mensagens.

## <a name="see-also"></a>Consulte também

[Análise de código para C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)