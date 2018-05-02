---
title: Criar um projeto de teste de unidade no Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d1add4084c856db5a31cf74d75ba848e50e30d3c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-unit-test-project"></a>Crie um projeto de teste de unidade

Geralmente, os testes de unidade refletem a estrutura do código que está sendo testado. Por exemplo, um projeto de teste de unidade será criado para cada projeto de código do produto. O projeto de teste pode estar na mesma solução que o código de produção ou em uma solução separada. É possível ter vários projetos de teste de unidade em uma solução.

> [!NOTE]
> O local dos testes de unidade para o código nativo e a estrutura do projeto de teste podem ser diferentes da estrutura descrita neste tópico. Para obter mais informações, consulte [Escrevendo testes de unidade para C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Para criar um projeto de teste de unidade:

1.  No menu **Arquivo**, escolha **Novo** e, em seguida, escolha **Projeto** (Teclado: Ctrl + Shift + N).

2.  Na caixa de diálogo Novo Projeto, expanda o nó **Instalado**, escolha o idioma que você deseja usar para o projeto de teste e escolha **Testar**.

3.  Para usar uma das estruturas de teste de unidade da Microsoft, escolha **Projeto de Teste de Unidade** na lista de modelos de projeto. Caso contrário, escolha o modelo de projeto da estrutura de teste de unidade que você deseja usar. Para testar o projeto Contas de nosso exemplo, você nomeará o projeto AccountsTests.

4.  No projeto de teste de unidade, adicione uma referência ao código que está sendo testado.  Veja como criar a referência a um projeto de código na mesma solução:

    1.  Selecione o projeto no Gerenciador de Soluções.

    2.  No menu **Projeto**, escolha **Adicionar Referência...**.

    3.  Na caixa de diálogo Gerenciador de Referência, abra o nó **Solução** e escolha **Projetos**. Verifique o nome do projeto de código e feche a caixa de diálogo.

5.  Se o código que você deseja testar estiver em outro local, consulte [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md) para obter informações sobre como adicionar referências.

## <a name="next-steps"></a>Próximas etapas
 **Escrevendo testes de unidade**

 Consulte uma das seguintes seções:

-   [Escrevendo testes de unidade para .NET Framework com a estrutura de teste de unidade Microsoft para código gerenciado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

-   [Escrever Testes de Unidade para C/C++](writing-unit-tests-for-c-cpp.md)

 **Executando testes de unidade**

- [Executar testes de unidade com o Gerenciador de Testes](../test/run-unit-tests-with-test-explorer.md)