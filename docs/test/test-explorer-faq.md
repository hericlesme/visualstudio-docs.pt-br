---
title: Perguntas frequentes do Gerenciador de Testes do Visual Studio | Microsoft Docs
ms.date: 1/15/2018
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: ghogen
ms.openlocfilehash: 1ca63ce299cb95546100e7f7ce7f98eb1c1616c2
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Perguntas frequentes sobre o Gerenciador de Testes do Visual Studio

## <a name="test-discovery"></a>Descoberta de Teste

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-are-dynamically-defined-for-example-theories-custom-adapters-custom-traits-ifdefs-etc-how-can-i-discover-these-tests"></a>1. O Gerenciador de Testes não está detectando meus testes definidos dinamicamente. (Por exemplo, teorias, adaptadores personalizados, características personalizadas, #ifdefs, etc.) Como descobrir estes testes?

  Compile o projeto e verifique se a descoberta de assembly está ativada em **Ferramentas > Opções > Testar**.

  [Detecção de Testes em Tempo Real](https://go.microsoft.com/fwlink/?linkid=862824) é a detecção de testes baseada na origem. Ela não consegue detectar testes que usam teorias, adaptadores personalizados, características personalizadas, instruções `#ifdef`, entre outros, porque esses itens são definidos em tempo de execução. Uma compilação é necessária para que esses testes sejam descobertos com precisão. Nas visualizações 15.6, a descoberta baseada em assembly (o detector tradicional) é executada somente depois de compilações. Essa configuração significa que a Detecção de Testes em Tempo Real detecta o máximo de testes possível durante a edição e a detecção baseada em assembly permite que os testes definidos de forma dinâmica apareçam após um build. A Descoberta de Teste em Tempo Real melhora a capacidade de resposta, mas ainda permite que você obtenha resultados completos e precisos após uma compilação.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. O que significa o '+' (sinal de mais) que aparece na linha superior do Gerenciador de Testes?

  O '+' (sinal de adição) indica que mais testes poderão ser detectados após um build se a detecção baseada em assembly estiver ativada. Ele será exibido quando forem detectados testes definidos dinamicamente no projeto.

  ![Linha de resumo do sinal de adição](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. A descoberta baseada em assembly não está mais funcionando para o projeto. Como ativar novamente?

  Acesse **Ferramentas > Opções > Testar** e marque a caixa **Adicionalmente, detectar testes de assemblies compilados após builds.**

  ![Opção baseada em assembly](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Agora os testes são exibidos no Gerenciador de Testes enquanto digito, sem a necessidade de compilar o projeto. O que mudou?

  Esse recurso chama-se [Descoberta de Teste em Tempo Real](https://go.microsoft.com/fwlink/?linkid=862824). Ele usa um analisador Roslyn para descobrir testes e popular o Gerenciador de Testes em tempo real, sem exigir que você compile o projeto. Para obter mais informações sobre o comportamento de detecção de testes para testes definidos dinamicamente, como teorias ou características personalizadas, confira a Pergunta frequente nº 1.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Quais linguagens e estruturas de teste podem usar a Descoberta de Teste em Tempo Real?

  [Descoberta de Teste em Tempo Real](https://go.microsoft.com/fwlink/?linkid=862824) só funciona para linguagens gerenciadas (C# e Visual Basic), pois é criada usando o compilador Roslyn. Por enquanto, a Descoberta de Teste em Tempo Real só funciona para as estruturas xUnit, NUnit e MSTest.

### <a name="6-how-can-i-turn-on-logs-for-the-test-explorer"></a>6. Como posso ativar logs para o Gerenciador de Testes?

  Navegue até **Ferramentas > Opções > Testar** e localize a seção Registro em Log.

### <a name="7-why-are-my-tests-in-uwp-projects-not-discovered-until-i-deploy-my-app"></a>7. Por que meus testes em projetos UWP não são detectados enquanto eu não implanto meu aplicativo?

  Os testes UWP têm como destino um tempo de execução diferente quando o aplicativo é implantado. Isso significa que para detectar testes com precisão em projetos UWP você precisa compilar seu projeto e também implantá-lo.

### <a name="8-how-does-sorting-test-results-work-in-the-hierarchy-view"></a>8. Como funciona a classificação de resultados de teste no modo de exibição de hierarquia?

  O modo de exibição de hierarquia classifica os testes em ordem alfabética e não por resultado. As outras configurações de agrupamento normalmente classificam os resultados de teste por resultado e, em seguida, em ordem alfabética. Veja o grupo diferente pelas opções na imagem a seguir para comparação. Você pode fornecer comentários sobre o design [neste assunto do GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

### <a name="9-in-the-hierarchy-view-there-are-passed-failed-skipped-and-not-run-icons-next-to-the-project-namespace-and-class-groupings-what-do-these-icons-mean"></a>9. Na exibição de hierarquia, há ícones passados, com falha, ignorados e não executados ao lado dos agrupamentos Projeto, Namespace e Classe. O que esses ícones significam?

  Os ícones ao lado dos agrupamentos Projeto, Namespace e Classe refletem o estado dos testes nesse agrupamento. Consulte a tabela a seguir.

  ![Ícones de Hierarquia do Gerenciador de Testes](media/testex-hierarchyicons.png)

## <a name="features"></a>Recursos

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Como ativar sinalizadores de recursos para experimentar os novos recursos de teste?

Sinalizadores de recursos são usados para enviar partes experimentais ou incompletas do produto para usuários ávidos que gostariam de fazer comentários antes que os recursos sejam fornecidos oficialmente. Eles podem desestabilizar a experiência de IDE. Use-os somente em ambientes de desenvolvimento seguros, como máquinas virtuais. Sinalizadores de recursos são sempre configurações que você usa por sua própria conta e risco. Você pode ativar recursos experimentais com a [extensão de Sinalizadores de Recursos](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) ou por meio do prompt de comando de desenvolvedor.

![Extensão de sinalizador de recursos](media/testex-featureflag.png)

Para ativar um sinalizador de recursos por meio do prompt de comando de desenvolvedor do Visual Studio, use o comando a seguir. Altere o caminho para onde o Visual Studio está instalado no computador e altere a chave do Registro para o sinalizador de recurso desejado.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Você pode desativar o sinalizador com o mesmo comando, usando o valor 0 em vez de 1 após dword.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Criar e Executar Testes de Unidade para Código Existente](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Efetuar teste de unidade em seu código](unit-test-your-code.md)
- [Perguntas Frequentes sobre os Testes de Unidade Dinâmicos](live-unit-testing-faq.md)