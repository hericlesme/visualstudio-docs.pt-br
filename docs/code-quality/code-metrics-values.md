---
title: Calcular métricas de código no Visual Studio
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3d0bf9b0bf689be847e7f16f2ee01db6e3df6d7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919059"
---
# <a name="code-metrics-values"></a>Valores de métricas de código

O aumento da complexidade de aplicativos modernos também aumenta a dificuldade de tornar o código sustentável e confiável. As métricas de código são um conjunto de medidas de software que fornecem aos desenvolvedores uma visão melhor do código que estão desenvolvendo. Aproveitando as métricas de código, os desenvolvedores podem compreender quais tipos de e/ou métodos devem ser reformulados ou mais totalmente testados. As equipes de desenvolvimento podem identificar possíveis riscos, entender o estado atual de um projeto e acompanhar o progresso durante o desenvolvimento de software.

Os desenvolvedores podem usar o Visual Studio para gerar dados de métricas de código que medem a complexidade e facilidade de manutenção de seu código gerenciado. Dados de métricas de código podem ser gerados para uma solução inteira ou um único projeto.

Para obter informações sobre como gerar dados de métricas de código no Visual Studio, consulte [como: gerar dados de métricas de código](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Medições de software

A lista a seguir mostra o código de resultados de métricas que calcula o Visual Studio:

- **Índice de facilidade de manutenção** -calcula um valor de índice entre 0 e 100 que representa a relativa facilidade de manutenção do código. Um valor alto significa melhor capacidade de manutenção. Classificações de codificados por cores podem ser usadas para identificar rapidamente pontos problemáticos em seu código. Uma classificação verde entre 20 e 100 e indica que o código tem boa facilidade de manutenção. Uma classificação amarela está entre 10 e 19 e indica que o código é razoavelmente fácil manutenção. Uma classificação vermelha é uma classificação entre 0 e 9 e indica pouca facilidade de manutenção.

- **A complexidade ciclomática** -mede a complexidade estrutural do código. Ela é criada pelo cálculo do número de caminhos de código diferente no fluxo do programa. Um programa com o fluxo de controle complexo exigirá mais testes para obter a cobertura de código válido e será menos manutenção.

- **Profundidade de herança** -indica o número de definições de classe que estende a raiz da hierarquia de classe. O maior hierarquia mais difícil seja entender onde determinados métodos e campos são definidos ou / e redefinido.

- **Classe acoplamento** -mede o acoplamento de classes exclusivos por meio de parâmetros, variáveis locais, tipos de retorno, chamadas de método, instanciações genéricas ou modelo, classes base, implementações de interface, campos definidos em tipos externos, e decoração do atributo. Bom design de software determina que tipos e métodos devem ter coesão alta e baixa acoplamento. Acoplamento alta indica um design que é difícil para reutilizar e manter devido a seus muitas interdependências em outros tipos.

- **Linhas de código** -indica o número aproximado de linhas no código. A contagem é baseada no código IL e, portanto, não o número exato de linhas no arquivo de código fonte. Um número muito alto pode indicar que um tipo ou método está tentando fazer muito trabalho e deve ser dividido. Ele também pode indicar que o tipo ou método pode ser difícil de manter.

## <a name="anonymous-methods"></a>Métodos anônimos

Um *método anônimo* é apenas um método que não tem nome. Métodos anônimos com mais frequência são usados para passar um bloco de código como um parâmetro de representante. Resultados de métricas para um método anônimo que é declarado em um membro, como um método ou o acessador, estão associados com o membro que declara o método. Eles não estão associados com o membro que chama o método.

Para obter mais informações sobre como as métricas de código trata métodos anônimos, consulte [métodos anônimos e análise de código](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Código gerado

Algumas ferramentas de software e compiladores geram código que é adicionado a um projeto e que o desenvolvedor do projeto não vê ou não deve ser alterada. Basicamente, métricas de código ignora o código gerado quando ela calcula os valores de métricas. Isso permite que os valores de métricas refletir o que o desenvolvedor pode ver e alterar.

Código gerado para formulários do Windows não é ignorado, porque ele é o código que o desenvolvedor pode ver e alterar.

## <a name="next-steps"></a>Próximas etapas

- [Como: gerar dados de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
- [Use a janela de resultados de métricas de código](../code-quality/working-with-code-metrics-data.md)