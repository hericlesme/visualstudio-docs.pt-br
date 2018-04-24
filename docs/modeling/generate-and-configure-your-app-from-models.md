---
title: Gerar e configurar o aplicativo por meio de modelos
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ace17c98bc0c65b2fea4daee778fdb8b278fa367
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="generate-and-configure-your-app-from-models"></a>Gerar e configurar o aplicativo por meio de modelos
Você pode gerar ou configurar as partes do seu aplicativo de um modelo.

 O modelo representa os requisitos mais diretamente o código. Derivando o comportamento do aplicativo diretamente do modelo, você pode responder a alterados requisitos de atualização muito mais rápida e confiável que o código. Embora algum trabalho inicial é necessário para configurar a derivação, esse investimento é retornado se você espera que as alterações nos requisitos ou se você planejar fazer diversas variantes do produto.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Gerando o código de seu aplicativo de um modelo
 É a maneira mais fácil de gerar código usando modelos de texto. Você pode gerar o código na mesma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução em que você mantenha o modelo. Para obter mais informações, consulte:

-   [Geração de código no tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

-   [Gerando código com base em uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)

 Esse método é fácil aplicar incrementalmente. Iniciar com um aplicativo que funciona somente em maiusculas ou minúsculas e escolha algumas partes dele que você deseja variar do modelo. Renomeie os arquivos de origem das partes para que eles se tornem arquivos de modelo (. TT) de texto. Neste ponto, os arquivos de origem. cs automaticamente serão gerados no arquivo de modelo, para que o aplicativo funcione como fazia antes.

 Você pode levar a uma parte do código e substitua-o por uma expressão de modelo de texto, que lê o modelo e gera essa parte do arquivo de origem. Pelo menos um valor do modelo deve gerar a fonte original para que, novamente, você pode executar o aplicativo e ele funcionará como antes. Depois de testar valores diferentes de modelo, você pode passar para inserir expressões de modelo em outra parte do código.

 Este método incremental significa que a geração de código geralmente é uma abordagem de baixo risco. Os aplicativos resultantes geralmente executam quase, bem como uma versão manual.

 No entanto, se você iniciar com um aplicativo existente, você perceberá que muitos de refatoração é necessário para separar os comportamentos diferentes que são controlados pelo modelo para que eles podem ser variados independentemente. É recomendável que você avalie esse aspecto do aplicativo quando você estimar o custo do seu projeto.

## <a name="configuring-your-application-from-a-model"></a>Configurar seu aplicativo de um modelo
 Se você deseja variar o comportamento do aplicativo em tempo de execução, você não pode usar a geração de código, que gera o código-fonte antes do aplicativo é compilado. Em vez disso, você pode projetar seu aplicativo para ler o modelo e variar seu comportamento adequadamente. Para obter mais informações, consulte:

-   [Como abrir um modelo partindo de um arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)

 Esse método também pode ser aplicado incrementalmente, mas há mais trabalho no início. Você precisa escrever o código que lerá o modelo e configurar uma estrutura que permite que seus valores estejam acessíveis para as partes de variável. Tornar as partes variável genérico é mais caro do que a geração de código.

 Normalmente, um aplicativo genérico executa menos bem suas contrapartes específico. Se o desempenho é crucial, seu plano de projeto deve incluir uma avaliação desse risco.

## <a name="developing-a-derived-application"></a>Desenvolvendo um aplicativo derivado
 As seguintes diretrizes gerais podem ser úteis.

-   **Iniciar específico, em seguida, generalizar.** Grave uma versão específica do seu aplicativo pela primeira vez. Esta versão deve funcionar em um conjunto de condições. Quando estiver satisfeito que ele está funcionando corretamente, você pode fazer com que algumas informações derivam de um modelo. Estenda as partes derivadas gradualmente.

     Por exemplo, crie um site que tem um conjunto específico de páginas da Web antes de criar um aplicativo Web que apresenta páginas que são definidas em um modelo.

-   **Os aspectos de variante do modelo.** Identifica os aspectos que variam entre uma implantação e outro, ou ao longo do tempo, como requisitos de alteração. Esses são os aspectos que devem ser derivados de um modelo.

     Por exemplo, se o conjunto de Web páginas e os links entre eles muda, mas o estilo e o formato das páginas é sempre o mesmo, em seguida, o modelo deve descrever os links, mas não tem que descrevem o formato das páginas.

-   **Preocupações separadas.** Se os aspectos de variável podem ser divididos em áreas independentes, use modelos separados para cada área. Usando ModelBus, você pode definir as operações que afetam os modelos e as restrições entre eles.

     Por exemplo, use um modelo para definir a navegação entre páginas da Web e um modelo diferente para definir o layout das páginas.

-   **O requisito, não a solução de modelo.** Crie o modelo para que ele descreve os requisitos de usuário. Por outro lado, não crie a notação de acordo com os aspectos de variável da implementação.

     Por exemplo, o modelo de navegação na Web deve representar páginas da Web e hiperlinks entre eles. O modelo de navegação na Web não deve representar a fragmentos de HTML ou classes em seu aplicativo.

-   **Gerar ou interpretar?** Se os requisitos de uma determinada implantação raramente serão alterados, gere código de programa do modelo. Se os requisitos podem mudar com frequência, ou podem coexistir em mais de uma variante na mesma implantação, grave o aplicativo para que ele possa ler e interpretar um modelo.

     Por exemplo, se você usar o modelo de site da Web para desenvolver uma série de sites diferentes e instalado separadamente, você deve gerar o código do site do modelo. Mas você usa o modelo para controlar um site que são alterados diariamente, em seguida, é melhor gravar um servidor Web que lê o modelo e apresenta o site adequadamente.

-   **UML ou DSL?** Considere a criação de sua notação de modelagem usando estereótipos para estender UML. Defina uma DSL se não houver nenhum diagrama UML que se adapta ao objetivo. Mas evitar dividir a semântica padrão de UML.

     Por exemplo, um diagrama de classe UML é uma coleção de caixas e setas; com essa notação pode teoricamente definir qualquer coisa. Mas não é recomendável que você use o diagrama de classe, exceto onde você é de fato que descreve um conjunto de tipos. Por exemplo, você pode adaptar a diagramas de classe para descrever os diferentes tipos de páginas da Web.

## <a name="see-also"></a>Consulte também

- [Gerando código com base em uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)
- [Como abrir um modelo partindo de um arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Geração de código no tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)