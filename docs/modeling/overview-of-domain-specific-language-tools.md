---
title: Visão geral das Ferramentas de Linguagem Específica do Domínio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 873c377b4b2262df6b12f581f1cdac901d27ffce
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859426"
---
# <a name="overview-of-domain-specific-language-tools"></a>Visão geral das Ferramentas de Linguagem Específica do Domínio
Ferramentas de linguagem específica do domínio (ferramentas DSL), que são hospedados no Visual Studio, permitem que você criar uma linguagem específica de domínio e, em seguida, gerar tudo o que os usuários devem ter para criar modelos que são baseados na linguagem.

 As ferramentas a seguir estão incluídas nas ferramentas de DSL:

-   Assistente de projeto que usa modelos de solução diferentes para ajudá-lo a começar a desenvolver sua linguagem específica do domínio.

-   Um designer gráfico para criar e editar sua definição de linguagem específica do domínio.

-   Um mecanismo de validação que verifica se a definição de linguagem específica de domínio está bem formada e exibe os erros e avisos se houver problemas.

-   Um gerador de código que usa uma definição de linguagem específica de domínio como entrada e produz o código-fonte como saída.

## <a name="the-dsl-tools-solution"></a>A solução de ferramentas DSL
 O Assistente de Designer específica de domínio fornece os seguintes modelos de solução:

-   Fluxo de tarefas

-   Diagramas de classe

-   Linguagem mínima

-   Modelos do componente

-   WPF mínima

-   Windows. Forms mínima

-   Biblioteca de DSL

 Para obter mais informações, consulte [escolhendo um modelo de solução de linguagem específica do domínio](../modeling/choosing-a-domain-specific-language-solution-template.md).

 O assistente cria uma solução do Visual Studio que tem os seguintes projetos:

-   DSL

     O projeto de Dsl define a linguagem específica de domínio e suas ferramentas de edição e de processamento.

-   **DslPackage**

     O projeto DslPackage determina como as ferramentas de linguagem integram com o Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>A Interface gráfica de ferramentas DSL
 Você pode usar a interface gráfica de ferramentas DSL para adicionar elementos e relações para sua linguagem específica do domínio. Depois que você adicionou os elementos, você pode definir sua aparência, mapeando-os para as formas, personalizar cores e adicionar os decoradores. Você também pode adicionar elementos à caixa de ferramentas.

## <a name="validation-in-dsl-tools"></a>Validação em ferramentas DSL
 DSL fornece um nível de validação para certificar-se de que o modelo de domínio atende aos requisitos básicos para geração de código. Normalmente, quando você cria sua própria linguagem específica de domínio, você adicionaria sua própria validação para expressar suas regras de lógica de negócios. Para obter mais informações sobre a validação personalizada, consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).

 É recomendável que você valide sua linguagem específica do domínio com frequência quando você criá-lo. Se sua linguagem específica do domínio tem erros de validação, você não pode gerar o código-fonte. O processo de geração de código-fonte dos modelos é executado clicando **transformar todos os modelos** na barra de ferramentas do Gerenciador de soluções. Sempre que você modificar a definição de linguagem, certifique-se **transformar todos os modelos**. Para obter mais informações, consulte [como: criar uma solução de linguagem específica do domínio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalização das ferramentas DSL
 Você pode fornecer código adicional para refinar o comportamento do modelo e definir restrições em seu idioma. Se necessário, você pode fazer alterações significativas, modificando os modelos de texto.

## <a name="distributing-your-dsl-solution"></a>Distribuir sua solução DSL
 Ferramentas DSL gera um pacote que está hospedado no Visual Studio. O pacote exibe uma caixa de ferramentas, um Gerenciador de DSL e outros elementos de interface do usuário que permitem aos usuários criar modelos usando sua linguagem específica do domínio.

 Quando você compila e executa a solução de DSL Tools no Visual Studio, uma segunda instância do Visual Studio mostra como sua linguagem específica do domínio será exibido para o usuário da linguagem. Depois de verificar se tudo está funcionando corretamente, você pode distribuir o `.vsix` arquivo que você encontrará na pasta de compilação do projeto DslPackage. Esse arquivo pode ser usado para instalar a DSL como uma extensão do Visual Studio em outros computadores.  Para obter mais informações, consulte [implantar soluções de linguagem específica do domínio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Consulte também

- [A instância experimental](../extensibility/the-experimental-instance.md)
- [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)