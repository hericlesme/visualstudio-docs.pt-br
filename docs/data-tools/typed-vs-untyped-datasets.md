---
title: Tipo vs. conjuntos de dados não tipados
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5819a208a54a5a4235330216e46b5e17f1260fa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="typed-vs-untyped-datasets"></a>Tipo vs. conjuntos de dados não tipados
Um conjunto de dados tipado é um conjunto de dados que primeiro é derivado da base de <xref:System.Data.DataSet> classe e, em seguida, usa as informações do **Dataset Designer**, que é armazenada em um arquivo. xsd, para gerar um novo fortemente tipado classe dataset. Informações do esquema (tabelas, colunas e assim por diante) são geradas e compiladas essa nova classe de conjunto de dados como um conjunto de propriedades e objetos de primeira classe. Como um conjunto de dados tipado herda da base de <xref:System.Data.DataSet> classe, a classe tipada pressupõe que todas as funcionalidades do <xref:System.Data.DataSet> de classe e pode ser usado com métodos que levam a uma instância de um <xref:System.Data.DataSet> classe como um parâmetro.

 Um conjunto de dados não tipado, por outro lado, não tem nenhum esquema interna correspondente. Como um conjunto de dados tipado, um conjunto de dados não digitado contém tabelas, colunas e assim por diante, mas aqueles são expostos somente como coleções. (No entanto, depois que você criar manualmente as tabelas e outros elementos de dados em um dataset não tipado, você pode exportar estrutura do conjunto de dados como um esquema usando o conjunto de dados <xref:System.Data.DataSet.WriteXmlSchema%2A> método.)

## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Acesso a dados em conjuntos de dados tipados e contrastantes
 A classe para um conjunto de dados tipado tem um modelo de objeto no qual suas propriedades assumir os nomes reais das tabelas e colunas. Por exemplo, se você estiver trabalhando com um conjunto de dados tipado, você pode fazer referência a uma coluna usando código como o seguinte:

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 Por outro lado, se você estiver trabalhando com um conjunto de dados não digitado, o código equivalente é:

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 Acesso de tipo não é apenas mais fáceis de ler, mas também totalmente suportados pelo IntelliSense no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Editor de código**. Além de ser mais fácil trabalhar com, a sintaxe para o conjunto de dados tipado fornece verificação de tipo em tempo de compilação, ele reduz a possibilidade de erros na atribuição de valores para os membros do conjunto de dados. Se você alterar o nome de uma coluna em sua <xref:System.Data.DataSet> classe e, em seguida, compilar o aplicativo, você receberá um erro de compilação. Clicando duas vezes sobre o erro de compilação no **lista de tarefas**, você poderá ir diretamente para a linha ou linhas de código que referenciam o nome de coluna antiga. Acesso a tabelas e colunas em uma conjunto de dados também é ligeiramente mais rápido em tempo de execução porque o acesso é determinado em tempo de compilação, não por meio de coleções em tempo de execução.

 Embora datasets tipados tem muitas vantagens, um conjunto de dados não tipado é útil em várias circunstâncias. O cenário mais óbvio é quando nenhum esquema está disponível para o conjunto de dados. Isso pode ocorrer, por exemplo, se seu aplicativo interage com um componente que retorna um conjunto de dados, mas você não souber com antecedência qual é sua estrutura. Da mesma forma, há ocasiões quando você estiver trabalhando com dados que não tem uma estrutura estática e previsível. Nesse caso, é muito prática se usar um conjunto de dados tipado, porque você precisa gerar a classe de conjunto de dados tipado com cada alteração na estrutura de dados.

 Geralmente, há muitas vezes quando você pode criar um conjunto de dados dinamicamente sem a necessidade de um esquema estão disponíveis. Nesse caso, o conjunto de dados é simplesmente uma estrutura conveniente no qual você pode manter informações, como os dados podem ser representados de maneira relacional. Ao mesmo tempo, você pode tirar proveito dos recursos do conjunto de dados, como a capacidade de serializar as informações para passar para outro processo ou para gravar um arquivo XML.

## <a name="see-also"></a>Consulte também

- [Ferramentas do conjunto de dados](../data-tools/dataset-tools-in-visual-studio.md)