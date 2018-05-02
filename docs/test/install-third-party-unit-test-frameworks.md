---
title: Instalar estruturas de teste de unidade de terceiros no Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 18667fe893c3007d1781e736054e9871cb767cfe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="install-third-party-unit-test-frameworks"></a>Instalar estruturas de teste de unidade de terceiros

O Gerenciador de Testes do Visual Studio pode executar qualquer estrutura de teste de unidade que desenvolveu uma interface de adaptador para o Gerenciador. O programa de instalação da estrutura instala os binários e adiciona modelos de projeto do Visual Studio para os idiomas que ele dá suporte. Quando você cria um projeto com o modelo, a estrutura é registrada com o Gerenciador de Testes. Uma solução do Visual Studio pode conter projetos de teste de unidade que usam diferentes estruturas e que são direcionados em diferentes idiomas. O Gerenciador de Testes executa todos eles.

## <a name="acquiring-third-party-frameworks"></a>Aquisição de estruturas de terceiros

Você pode baixar e instalar diversas estruturas de teste de unidade de terceiros usando o Gerenciador de Extensões do Visual Studio ou o Visual Studio Marketplace. Estruturas também podem ser baixadas de outros sites, como o site da estrutura.

### <a name="installing-from-visual-studio"></a>Instalação do Visual Studio

1. Escolha **Ferramentas** no menu padrão e, em seguida, selecione **Extensões e atualizações**.

2. Expanda **Online** > **Visual Studio Marketplace** > **Ferramentas**. Escolha **Teste**.

3. Navegue pela lista para localizar a estrutura.

4. Selecione a estrutura e escolha **Download**.

Para obter mais informações, consulte [Localizando e Usando Extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Instalação da Web

Se você souber a estrutura em que você está interessado:

1. Abra [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Digite o nome da estrutura na caixa **Localizar**.

3. Escolha a estrutura na lista de resultados para navegar até a página do Visual Studio Marketplace da ferramenta.

Para procurar uma lista de estruturas juntamente com outras ferramentas de teste:

1. Abra [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Em **Filtrar por categoria/coleção**, escolha **Ver tudo**.

3. Na lista **Categoria** (rotulada como **Mostrando**), expanda o nó **Ferramentas** e, em seguida, escolha **Teste**.

4. Escolha uma estrutura na lista de resultados para navegar até uma página do Visual Studio Marketplace da ferramenta.

## <a name="see-also"></a>Consulte também

- [Efetuar teste de unidade em seu código](../test/unit-test-your-code.md)
