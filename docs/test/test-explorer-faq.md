---
title: Perguntas Frequentes do Gerenciador de Teste | Microsoft Docs
ms.date: 1/15/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
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
ms.openlocfilehash: db3cf85576e6c46aca14897f7244cd0f56d8d5c2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Perguntas frequentes sobre o Gerenciador de Testes do Visual Studio

## <a name="test-discovery"></a>Descoberta de Teste

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-have-theories-custom-adapters-custom-traits-use-ifdefs-or-are-dynamically-defined-how-can-i-discover-these-tests"></a>1. O Gerenciador de Testes não está descobrindo meus testes que têm teorias, adaptadores personalizados, características personalizadas, usam #ifdefs ou são definidos dinamicamente. Como descobrir estes testes?

  Compile o projeto e verifique se a descoberta de assembly está ativada em **Ferramentas > Opções > Testar**.

  [Descoberta de Teste em Tempo Real](https://go.microsoft.com/fwlink/?linkid=862824), que é a descoberta de teste baseada no código-fonte, não pode descobrir testes que usam teorias, adaptadores personalizados, características personalizadas, instruções `#ifdef` ou que são definidos dinamicamente de alguma outra maneira. Uma compilação é necessária para que esses testes sejam descobertos com precisão. Nas visualizações 15.6, a descoberta baseada em assembly (o detector tradicional) é executada somente depois de compilações. Isso significa que a Descoberta de Teste em Tempo Real detecta tantos testes quantos puder enquanto você estiver editando, e a descoberta baseada em assembly permite que as teorias (ou quaisquer testes definidos de forma dinâmica) apareçam após uma compilação. A Descoberta de Teste em Tempo Real melhora a capacidade de resposta, mas ainda permite que você obtenha resultados completos e precisos após uma compilação.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. O que significa o '+' (sinal de mais) que aparece na linha superior do Gerenciador de Testes?

  O '+' (sinal de adição) indica que mais testes poderão ser descobertos após uma compilação se descoberta baseada em assembly estiver ativada. Ele será exibido se testes definidos dinamicamente forem detectados no projeto.

  ![Linha de resumo do sinal de adição](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. A descoberta baseada em assembly não está mais funcionando para o projeto. Como ativar novamente?

  Vá para **Ferramentas > Opções > Testar** e marque a caixa **Além disso, descubra testes de assemblies compilados após builds.**

  ![Opção baseada em assembly](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Agora os testes são exibidos no Gerenciador de Testes enquanto digito, sem a necessidade de compilar o projeto. O que mudou?

  Esse recurso chama-se [Descoberta de Teste em Tempo Real](https://go.microsoft.com/fwlink/?linkid=862824). Ele usa um analisador Roslyn para descobrir testes e popular o Gerenciador de Testes em tempo real, sem exigir que você compile o projeto. Confira o item n º 1 das Perguntas Frequentes para obter mais informações sobre o comportamento de detecção de teste para testes definidos dinamicamente, como teorias ou características personalizadas.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Quais linguagens e estruturas de teste podem usar a Descoberta de Teste em Tempo Real?

  [Descoberta de Teste em Tempo Real](https://go.microsoft.com/fwlink/?linkid=862824) só funciona para linguagens gerenciadas (C# e Visual Basic), pois é criada usando o compilador Roslyn. Por enquanto, a Descoberta de Teste em Tempo Real só funciona para as estruturas xUnit, NUnit e MSTest.

## <a name="features"></a>Recursos

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Como ativar sinalizadores de recursos para experimentar os novos recursos de teste?

Sinalizadores de recursos são usados para enviar partes experimentais ou incompletas do produto para usuários ávidos que gostariam de fazer comentários antes que os recursos sejam fornecidos oficialmente. Eles podem desestabilizar a experiência de IDE. É recomendável usá-los somente em ambientes de desenvolvimento seguros, como máquinas virtuais. Sinalizadores de recursos são sempre configurações que você usa por sua própria conta e risco. Você pode ativar recursos experimentais com a [extensão de Sinalizadores de Recursos](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) ou por meio do prompt de comando de desenvolvedor.

![Extensão de sinalizador de recursos](media/testex-featureflag.png)

Para ativar um sinalizador de recursos por meio do prompt de comando de desenvolvedor do Visual Studio, use o comando a seguir. Altere o caminho para onde o Visual Studio está instalado no computador e altere a chave do Registro para o sinalizador de recurso desejado.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Você pode desativar o sinalizador com o mesmo comando, usando o valor 0 em vez de 1 após dword.
  
## <a name="see-also"></a>Consulte também

<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>  
[Criar e executar testes de unidade para código existente](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
[Testar código de unidade](unit-test-your-code.md)
[Perguntas frequentes sobre Live Unit Testing](live-unit-testing-faq.md)
