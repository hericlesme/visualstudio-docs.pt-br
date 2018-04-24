---
title: Substituindo e estendendo as classes geradas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 77a33546d02738ae03e4da5180aa15e2b94f91ea
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="overriding-and-extending-the-generated-classes"></a>Substituindo e estendendo as classes geradas
A definição de DSL é uma plataforma na qual você pode criar um conjunto poderoso de ferramentas se baseiam em uma linguagem específica de domínio. Muitas extensões e adaptações podem ser feitas por substituir e estender as classes que são geradas a partir da definição de DSL. Essas classes incluem não apenas as classes de domínio que você definiu explicitamente no diagrama DSL definição, mas também a outras classes que definem a caixa de ferramentas, explorer, serialização e assim por diante.

## <a name="extensibility-mechanisms"></a>Mecanismos de extensibilidade
 Vários mecanismos são fornecidos para permitir que você estenda o código gerado.

### <a name="overriding-methods-in-a-partial-class"></a>Substituir métodos em uma classe parcial
 Definições de classes parciais permitem que uma classe seja definida em mais de um único local. Isso permite que você separe o código gerado do código que você escrever por conta própria. No seu código escrito manualmente, você pode substituir classes herdadas pelo código gerado.

 Por exemplo, se em sua definição de DSL definir uma classe de domínio chamada `Book`, você poderia escrever código personalizado que adiciona métodos de substituição:

 `public partial class Book`

 `{`

 `protected override void OnDeleting()`

 `{`

 `MessageBox.Show("Deleting book " + this.Title);`

 `base.OnDeleting();`

 `} }`

> [!NOTE]
>  Para substituir os métodos em uma classe gerada, sempre grave seu código em um arquivo separado de arquivos gerados. Normalmente, o arquivo está contido em uma pasta denominada CustomCode. Se você fizer alterações no código gerado, elas serão perdidas quando você gerar novamente o código da definição de DSL.

 Para descobrir quais métodos que você pode substituir, digite **substituir** na classe, seguido por um espaço. A dica de ferramenta do IntelliSense informará quais métodos podem ser substituídos.

### <a name="double-derived-classes"></a>Classes derivadas de duplo
 A maioria dos métodos em classes geradas é herdada de um conjunto fixo de classes nos namespaces de modelagem. No entanto, alguns métodos são definidos no código gerado. Em geral, isso significa que você não pode substituí-los; Você não pode substituir em uma classe parcial os métodos que são definidos em outra definição parcial da mesma classe.

 No entanto, você pode substituir esses métodos, definindo o **gera duplo derivado** sinalizador para a classe de domínio. Esta faz com que duas classes a serem gerados, sendo uma classe base abstrata da outra. Todas as definições de método e propriedade são na classe base, e é apenas o construtor na classe derivada.

 Por exemplo, no exemplo Library.dsl, o `CirculationBook` classe de domínio tem a `Generates``Double Derived` propriedade definida como `true`. O código gerado para essa classe de domínio contém duas classes:

-   `CirculationBookBase`, que é um resumo e que contém todos os métodos e propriedades.

-   `CirculationBook`, que é derivada de `CirculationBookBase`. Ele está vazio, exceto seus construtores.

 Para substituir qualquer método, você cria uma definição parcial da classe derivada como `CirculationBook`. Você pode substituir os métodos gerados e métodos herdados da estrutura de modelagem.

 Você pode usar esse método com todos os tipos de elemento, incluindo conectores, relações, formas, diagramas e elementos de modelo. Você também pode substituir os métodos de outras classes geradas. Algumas classes geradas, como o ToolboxHelper sempre são derivados de duplo.

### <a name="custom-constructors"></a>Construtores personalizados
 Você não pode substituir um construtor. Mesmo em classes derivadas de duplo, o construtor deve ser na classe derivada.

 Se você quiser fornecer sua própria construtor, você pode fazer isso definindo `Has Custom Constructor` para a classe de domínio na definição de DSL. Quando você clica em **transformar todos os modelos**, o código gerado não incluirá um construtor para essa classe. Ele inclui uma chamada para o construtor ausente. Isso faz com que um relatório de erros ao compilar a solução. Clique duas vezes o relatório de erros para ver um comentário no código gerado que explica o que você deve fornecer.

 Gravar uma definição de classe parcial em um arquivo que é separado dos arquivos gerados e fornecer o construtor.

### <a name="flagged-extension-points"></a>Pontos de extensão sinalizados
 Um ponto de extensão sinalizados é um lugar na definição de DSL onde você pode definir uma propriedade ou uma caixa de seleção para indicar que você irá fornecer um método personalizado. Construtores personalizados são um exemplo. Outros exemplos incluem configuração o `Kind` da propriedade de ser calculado ou armazenamento personalizado ou configuração de **personalizado é** sinalizador no construtor de uma conexão.

 Em cada caso, quando você define o sinalizador e gerar novamente o código, compilação ocorrerá um erro. Clique duas vezes o erro para ver um comentário que explica o que você precisa fornecer.

### <a name="rules"></a>Regras
 O Gerenciador de transações permite que você defina regras que são executados antes do final de uma transação na qual designado Ocorreu um evento, como uma alteração em uma propriedade. Regras normalmente são usadas para manter synchronism entre os elementos no repositório. Por exemplo, as regras são usadas para certificar-se de que o diagrama exibe o estado atual do modelo.

 As regras são definidas em uma base por classe, para que você não precisa ter o código que registra a regra para cada objeto. Para obter mais informações, consulte [regras propagar as alterações no modelo de](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Eventos de armazenamento
 O repositório de modelagem fornece um mecanismo de eventos que você pode usar para escutar para tipos específicos de alteração no armazenamento, incluindo a adição e exclusão de elementos, as alterações nos valores de propriedade e assim por diante. Os manipuladores de eventos são chamados após o encerramento da transação em que as alterações foram feitas. Normalmente, esses eventos são usados para atualizar recursos fora da loja.

### <a name="net-events"></a>Eventos do .NET
 Você pode se inscrever para alguns eventos em formas. Por exemplo, você pode ouvir cliques do mouse em uma forma. Você precisa escrever código que assina o evento para cada objeto. Esse código pode ser escrito em uma substituição de InitializeInstanceResources().

 Alguns eventos são gerados no ShapeFields, que são usadas para desenhar uma forma decoradores. Para obter um exemplo, consulte [como: interceptar um clique em uma forma ou um decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

 Esses eventos geralmente não ocorrem dentro de uma transação. Se você quiser fazer alterações no repositório, você deve criar uma transação.