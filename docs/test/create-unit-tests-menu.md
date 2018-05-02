---
title: Criar stubs de método de teste de unidade no Visual Studio
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 39c59d76d10c2028214b2a1ea15ff139000e3080
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Criar stubs de método de teste de unidade com o comando Criar Testes de Unidade

O comando **Criar Testes de Unidade** do Visual Studio fornece a capacidade de criar stubs de método de teste de unidade. Esse recurso permite a configuração fácil de um projeto de teste, da classe de teste e do stub do método de teste dentro dele.

## <a name="availability-and-extensions"></a>Disponibilidade e extensões

O comando de menu **Criar Testes de Unidade**:

* Está disponível nas edições Community, Professional e Enterprise do Visual Studio 2015 e posteriores.

* Dá suporte apenas ao código C# destinado ao .NET Framework.

* É extensível e dá suporte à emissão de testes nos formatos MSTest, MSTest V2, NUnit e xUnit.

## <a name="get-started"></a>Introdução

Para começar, selecione um método, um tipo ou um namespace no editor de código no projeto que você deseja testar, abra o menu de atalho e escolha **Criar Testes de Unidade**. Isso abre a caixa de diálogo **Criar Testes de Unidade** em que as opções de criação para os novos testes de unidade podem ser selecionadas.

![Usando o comando Criar testes de unidade](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Configurando as características do teste de unidade

Se você planeja executar esses testes como parte do processo de automação de teste, você poderá considerar criar o teste em outro projeto de teste (a segunda opção na caixa de diálogo acima) e configurar as características do teste de unidade para o teste de unidade. Isso permitirá que você inclua ou exclua mais facilmente esses testes específicos como parte de uma integração contínua ou pipeline de implantação contínua. As características são definidas pela adição de metadados ao teste de unidade diretamente, conforme mostrado abaixo.

![Configurando as características do teste de unidade](media/createunittest.png)

## <a name="using-third-party-unit-test-frameworks"></a>Usando estruturas de teste de unidade de terceiros

Com o Visual Studio, você pode facilmente criar testes de unidade usando qualquer estrutura de teste. Para instalar outras estruturas de teste:

1. Escolha **Ferramentas** > **Extensões e Atualizações**.
2. Expanda **Online** > **Visual Studio Marketplace** > **Ferramentas** e, em seguida, escolha **Testes**.

![Usando estruturas de teste de terceiros](media/createunittestfx.png)

As extensões da estrutura de teste também estão disponíveis no Visual Studio Marketplace:

* [Extensão do NUnit para geradores de teste](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Extensão do xUnit.net para geradores de teste](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Quando devo usar esse recurso?

Use este recurso sempre que precisar criar testes de unidade, mas especialmente quando estiver testando o código existente que tem muito pouca ou nenhuma cobertura do teste e nenhuma documentação. Em outras palavras, onde há uma especificação de código limitada ou inexistente. Ele implementa efetivamente uma abordagem semelhante aos [Testes de Unidade Inteligentes](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) que caracterizam o comportamento observado do código.

No entanto, esse recurso é igualmente aplicável para a situação em que o desenvolvedor começa escrevendo um código e o usa para inicializar a disciplina de teste de unidade. Dentro do fluxo de codificação, o desenvolvedor talvez queira criar rapidamente um stub de método de teste de unidade (com uma classe de teste adequada e um projeto de teste adequado) para uma determinada parte do código.

## <a name="see-also"></a>Consulte também

- [Criar stubs de método de teste de unidade com "Criar testes de unidade"](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Postagens de blog sobre testes de unidade](https://blogs.msdn.microsoft.com/devops/?s=unit+testing)
