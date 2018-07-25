---
title: Introdução à edição no Visual Studio
ms.date: 11/30/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 265e0a4c596a78e53de6fe92d837796f2e52a703
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079142"
---
# <a name="quickstart-use-the-code-editor"></a>Início rápido: Usar o editor de códigos

Nesta introdução de 10 minutos ao editor de código do Visual Studio, adicionaremos o código a um arquivo para ver algumas das formas pelas quais o Visual Studio facilita a escrita, a navegação e o entendimento do código.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

Este início rápido pressupõe que você já esteja familiarizado com uma linguagem de programação. Se não estiver, sugerimos que você confira um dos tutoriais de programação, por exemplo, como criar um aplicativo Web com [Python](../ide/quickstart-python.md) ou [C#](../ide/tutorial-csharp-aspnet-core.md), ou criar um aplicativo de console com [Visual Basic](../ide/quickstart-visual-basic-console.md) ou [C++](../ide/getting-started-with-cpp-in-visual-studio.md).

## <a name="create-a-new-code-file"></a>Criar um novo arquivo de código

Comece criando um novo arquivo e adicionando códigos nele.

1. Abra o Visual Studio e, no menu **Arquivo** na barra de menus, selecione **Novo** > **Arquivo**.

1. Na caixa de diálogo **Novo Arquivo**, na categoria **Geral**, escolha **Classe do Visual C#** e, então, selecione **Abrir**.

   Um novo arquivo é aberto no editor com o esqueleto de uma classe de C#. (Observe que não precisamos criar um projeto completo do Visual Studio para obter alguns dos benefícios que o editor de códigos oferece; basta ter um arquivo de código!)

   ![Arquivo de código C# no Visual Studio](media/quickstart-editor.png)

## <a name="use-code-snippets"></a>Usar trechos de código

O Visual Studio fornece *trechos de código* úteis que você pode usar para gerar os blocos de código usados com frequência de forma rápida e fácil. Os [trechos de código](../ide/code-snippets.md) estão disponíveis para linguagens de programação diferentes, incluindo C#, Visual Basic e C++. Vamos adicionar o trecho `void Main` de C# em nosso arquivo.

1. Coloque o cursor logo acima da chave de fechamento final **}** no arquivo e digite os caracteres `svm` (que significam `static void Main`&mdash;não se preocupe muito se você não sabe o que isso significa).

   Uma caixa de diálogo pop-up é exibida com informações sobre o trecho de código `svm`.

   ![IntelliSense para o trecho de código no Visual Studio](media/quickstart-intellisense-snippet.png)

1. Pressione a **Guia** duas vezes para inserir o trecho de código.

   Você verá que a assinatura do método `static void Main()` será adicionada ao arquivo. O método [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) é o ponto de entrada para aplicativos C#.

Os trechos de código disponíveis variam em linguagens de programação diferentes. Examine os trechos de código disponíveis para a linguagem escolhendo **Editar** > **IntelliSense** > **Inserir Trecho** e, em seguida, escolhendo a pasta da linguagem. Para o C#, a lista tem este aspecto:

![Lista de trecho de código de C#](media/quickstart-code-snippet-list.png)

A lista inclui trechos para a criação de uma [classe](/dotnet/csharp/programming-guide/classes-and-structs/classes), um [construtor](/dotnet/csharp/programming-guide/classes-and-structs/constructors), um loop [for](/dotnet/csharp/language-reference/keywords/for), uma instrução [if](/dotnet/csharp/language-reference/keywords/if-else) ou [switch](/dotnet/csharp/language-reference/keywords/switch) e muito mais.

## <a name="comment-out-code"></a>Comentar o código

A barra de ferramentas, que é a linha de botões sob a barra de menus no Visual Studio, pode ajudar a aumentar sua produtividade durante a codificação. Por exemplo, você pode alternar o modo de preenchimento do IntelliSense (o [IntelliSense](using-intellisense.md) é um recurso de codificação que exibe uma lista de correspondência de métodos, entre outras coisas), aumentar ou diminuir um recuo de linha ou comentar um código que você não deseja compilar. Nesta seção, comentaremos alguns códigos.

![Barra de ferramentas do editor](media/quickstart-editor-toolbar.png)

1. Cole o código a seguir no corpo do método `Main()`.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. Não estamos usando a variável `morewords`, mas podemos usá-la mais tarde. Portanto, não queremos excluí-la por completo. Em vez disso, vamos comentar as linhas. Selecione a definição inteira de `morewords` até o ponto e vírgula de fechamento e, em seguida, escolha o botão **Comentar as linhas selecionadas** na barra de ferramentas. Caso prefira usar o teclado, pressione **Ctrl**+**K**, **Ctrl**+**C**.

   ![Botão de comentários](media/quickstart-comment-out.png)

   Os caracteres de comentários `//` de C# são adicionados ao início de cada linha selecionada para comentar o código.

## <a name="collapse-code-blocks"></a>Recolher blocos de código

Não queremos ver o [construtor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) vazio para `Class1` que foi gerado. Portanto, para desobstruir nossa exibição do código, vamos recolhê-la. Escolha a pequena caixa cinza com o sinal de subtração dentro da margem da primeira linha do construtor. Ou, se você for um usuário de teclado, posicione o cursor em qualquer lugar no código do construtor e pressione **Ctrl**+**M**, **Ctrl**+**M**.

![Botão Recolher estrutura de tópicos](media/quickstart-collapse.png)

O bloco de código é recolhido apenas na primeira linha, seguido por um sinal de reticências (`...`). Para expandir o bloco de código novamente, clique na mesma caixa cinza que agora tem um sinal de adição ou pressione **Ctrl**+**M**, **Ctrl**+**M** novamente. Esse recurso é chamado de [Estrutura de tópicos](../ide/outlining.md) e é útil principalmente ao recolher métodos longos ou classes inteiras.

## <a name="view-symbol-definitions"></a>Exibir definições de símbolo

O editor do Visual Studio facilita a inspeção da definição de um tipo, de um método, etc. Uma maneira é navegar até o arquivo que contém a definição, por exemplo, ao selecionar **Ir para Definição** em qualquer lugar em que o símbolo esteja referenciado. Uma maneira ainda mais rápida que não move o foco para fora do arquivo em que você está trabalhando é usar a opção [Inspecionar Definição](../ide/go-to-and-peek-definition.md#peek-definition). Vamos espiar a definição do tipo `string`.

1. Clique com o botão direito do mouse em qualquer ocorrência de `string` e escolha **Espiar Definição** no menu de conteúdo. Se preferir, pressione **Alt**+**F12**.

   Uma janela pop-up será exibida com a definição da classe `String`. Você pode rolar na janela pop-up ou até mesmo inspecionar a definição de outro tipo do código inspecionado.

   ![Inspecionar janela de definição](media/quickstart-peek-definition.png)

1. Feche a janela de definição inspecionada ao selecionar a caixa pequena com um “x” no canto superior direito da janela pop-up.

## <a name="use-intellisense-to-complete-words"></a>Usar o IntelliSense para completar palavras

O [IntelliSense](../ide/using-intellisense.md) é um recurso valioso quando você está gravando o código. Ele pode mostrar informações sobre membros disponíveis de um tipo ou detalhes de parâmetros para sobrecargas diferentes de um método. Você também pode usar o IntelliSense para completar uma palavra depois que você digitar caracteres suficientes para desambiguá-la. Vamos adicionar uma linha de código para imprimir as cadeias de caracteres ordenadas na janela de console, que é o local padrão para envio da saída do programa.

1. Abaixo da variável `query`, comece a digitar o código a seguir:

   ```csharp
   foreach (string str in qu
   ```

   Você verá o IntelliSense mostrar as **Informações Rápidas** sobre o símbolo `query`.

   ![Preenchimento de palavras do IntelliSense no Visual Studio](media/quickstart-intellisense-completion-list.png)

1. Para inserir o restante da palavra `query` usando a funcionalidade de preenchimento de palavras do IntelliSense, pressione **Tab**.

1. Finalize o bloco de código para que ele se pareça com o seguinte código. Você mesmo pode praticar usando os trechos de código novamente ao inserir `cw` e, então, pressionar a **Guia** duas vezes para gerar o código `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refatorar um nome

Ninguém obtém o código correto na primeira vez e uma das coisas que talvez você precise alterar é o nome de uma variável ou de um método. Vamos experimentar a funcionalidade de [refatorar](../ide/refactoring-in-visual-studio.md) do Visual Studio para renomear a variável `_words` como `words`.

1. Coloque o cursor sobre a definição da variável `_words` e selecione **Renomear** ao clicar com o botão direito do mouse ou no menu de contexto, ou ao pressionar **Ctrl**+**R**, **Ctrl**+**R**.

   Uma caixa de diálogo pop-up chamada **Renomear** aparecerá no canto superior direito do editor.

1. Insira o nome desejado **words**. Observe que a referência ao `words` na consulta também será renomeada automaticamente. Antes de pressionar **Enter**, marque a caixa de seleção **Incluir Comentários** na caixa pop-up **Renomear**.

   ![Caixa de diálogo Renomear](media/quickstart-rename.png)

1. Pressione **ENTER**.

   As duas ocorrências de `words` foram renomeadas, bem como a referência ao `words` do comentário de código.

## <a name="next-steps"></a>Próximas etapas

Você concluiu este Início Rápido do editor do Visual Studio. Em seguida, experimente alguns dos outros Inícios Rápidos do ambiente de desenvolvimento do Visual Studio, como [Início Rápido: Projetos e soluções](../ide/quickstart-projects-solutions.md) ou [Início Rápido: Personalizar o Visual Studio](../ide/quickstart-personalize-the-ide.md), veja mais maneiras de [Navegar pelo código](../ide/navigating-code.md) ou confira os links para obter mais informações sobre os recursos abordados. Caso contrário, boa codificação!

## <a name="see-also"></a>Consulte também

- [Início rápido: Introdução ao IDE do Visual Studio](../ide/quickstart-ide-orientation.md)
- [Início Rápido: Personalizar o Visual Studio](../ide/quickstart-personalize-the-ide.md)
- [Início rápido: projetos e soluções](../ide/quickstart-projects-solutions.md)
- [Trechos de código](../ide/code-snippets.md)
- [Estrutura de tópicos](../ide/outlining.md)
- [Ir para Definição e Definição de Pico](../ide/go-to-and-peek-definition.md)
- [Refatoração](../ide/refactoring-in-visual-studio.md)
- [Usar o IntelliSense](../ide/using-intellisense.md)
