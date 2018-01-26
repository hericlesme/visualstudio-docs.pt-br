---
title: "Introdução à edição no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: fd24e4ebcdda7a3b8fbc0b992e1ef952a930029a
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="quickstart-coding-in-the-editor"></a>Guia de início rápido: Codificação no editor

Nesta introdução de 10 minutos ao editor, vamos adicionar o código a um arquivo para ver algumas das formas em que o Visual Studio facilita a gravação, a navegação e o entendimento do código.

## <a name="create-a-new-code-file"></a>Criar um novo arquivo de código

Comece criando um novo arquivo e adicionando códigos nele. Observe que não precisamos criar um projeto para obter alguns dos benefícios que o editor oferece.

1. Abra o Visual Studio e, do menu **Arquivo** na barra de menus, selecione **Novo** > **Arquivo...**

1. Na caixa de diálogo **Novo Arquivo**, na categoria **Geral**, escolha **Classe do Visual C#** e, então, selecione **Abrir**.

   Um novo arquivo é aberto no editor com o esqueleto de uma classe de C#.

## <a name="using-code-snippets"></a>Usando trechos de código

O Visual Studio fornece trechos de código úteis que você pode usar para gerar os blocos de código usados com frequência de forma rápida e fácil. Os [trechos de código](../ide/code-snippets.md) estão disponíveis para linguagens de programação diferentes, incluindo C#, Visual Basic e C++. Vamos adicionar o trecho `void Main` de C# em nosso arquivo.

1. Coloque o cursor abaixo da chave de fechamento do construtor `Class1` e insira os caracteres `svm`.

   Você verá uma caixa de diálogo do IntelliSense aparecer com informações sobre o trecho `svm`.

   ![Trecho do IntelliSense](media/quickstart-intellisense-snippet.png)

1. Pressione a **Guia** duas vezes para inserir o trecho de código.

   Você verá que a assinatura do método `static void Main()` será adicionada ao arquivo. O método `Main()` é o ponto de entrada dos aplicativos de C#.

Os trechos de código disponíveis variam para linguagens diferentes. Você pode examinar os trechos de código disponíveis para sua linguagem de programação, selecionando **Editar**, **IntelliSense**, **Inserir trecho...** e, em seguida, escolhendo a pasta da sua linguagem. Para o C#, a lista tem este aspecto:

![Lista de trecho de código de C#](media/quickstart-code-snippet-list.png)

A lista inclui os trechos de código para criar uma classe, um construtor, um `Console.WriteLine()`, loops `for`, instruções `if` e `switch`, e muito mais.

## <a name="commenting-out-code"></a>Comentando o código

A barra de ferramentas fornece uma série de botões para aumentar sua produtividade conforme você codifica. Por exemplo, você pode alternar o modo de conclusão do IntelliSense, aumentar ou diminuir um recuo, definir um indicador ou comentar um código. Nesta seção, comentaremos alguns códigos que não queremos compilar.

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
    }

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

1. Não estamos usando a variável `morewords`, mas podemos usá-la posteriormente, então não queremos excluí-la. Em vez disso, vamos comentar as linhas. Selecione a definição inteira de `morewords` até o ponto e vírgula de fechamento e, em seguida, selecione o botão **Comentar as linhas selecionadas** na barra de ferramentas ou pressione **Ctrl**+**K**, **Ctrl**+**C**.

   ![Botão de comentários](media/quickstart-comment-out.png)

   Os caracteres de comentários `//` de C# são adicionados ao início de cada linha selecionada para comentar o código.

## <a name="collapsing-code-blocks"></a>Recolhendo blocos de código

Nós não queremos ver o construtor vazio para `Class1` que foi gerado. Então, para desobstruir nossa exibição do código, vamos recolhê-la. Escolha a pequena caixa cinza com o sinal de subtração dentro da margem da primeira linha do construtor. Ou, se você for um usuário de teclado, posicione o cursor em qualquer lugar no código do construtor e pressione **Ctrl**+**M**, **Ctrl**+**M**.

![Botão Recolher estrutura de tópicos](media/quickstart-collapse.png)

O bloco de código é recolhido apenas na primeira linha, seguido por um sinal de reticências (`...`). Para expandir o bloco de código novamente, clique na mesma caixa cinza que agora tem um sinal de adição ou pressione **Ctrl**+**M**, **Ctrl**+**M** novamente. Esse recurso é chamado de [estrutura de tópicos](../ide/outlining.md) e é especialmente útil quando você estiver recolhendo métodos longos ou classes inteiras.

## <a name="viewing-symbol-definitions"></a>Exibindo definições de símbolo

O editor do Visual Studio facilita a inspeção da definição de um tipo, de um método, etc. Uma maneira é navegar até o arquivo que contém a definição, por exemplo, ao selecionar **Ir para Definição** em qualquer lugar em que o símbolo esteja referenciado. Uma maneira ainda mais rápida que não move o foco para fora do arquivo em que você está trabalhando é usar a opção [Inspecionar Definição](../ide/go-to-and-peek-definition.md#peek-definition). Vamos inspecionar a definição de `string`.

1. Clique com botão direito do mouse em qualquer ocorrência do `string` e selecione **Inspecionar Definição** no menu de conteúdo&mdash; ou pressione **Alt**+**F12**.

   Uma janela pop-up será exibida com a definição da classe `String`. Você pode rolar na janela pop-up ou até mesmo inspecionar a definição de outro tipo do código inspecionado.

   ![Inspecionar janela de definição](media/quickstart-peek-definition.png)

1. Feche a janela de definição inspecionada ao selecionar a caixa pequena com um “x” no canto superior direito da janela pop-up.

## <a name="using-intellisense-to-complete-words"></a>Usando o IntelliSense para completar palavras

O [IntelliSense](../ide/using-intellisense.md) é um recurso valioso quando você está gravando o código. Ele pode mostrar informações sobre membros disponíveis de um tipo ou detalhes de parâmetros para sobrecargas diferentes de um método. Você também pode usar o IntelliSense para completar uma palavra depois que você digitar caracteres suficientes para desambiguá-la. Vamos adicionar uma linha de código para imprimir as cadeias de caracteres ordenadas na janela do console.

1. Abaixo da variável `query`, comece a digitar o código a seguir:

   ```csharp
   foreach (string str in qu
   ```

   Você verá o IntelliSense mostrar as **Informações Rápidas** sobre o símbolo `query`.

   ![Palavra do IntelliSense completa](media/quickstart-intellisense-completion-list.png)

1. Para inserir o restante da palavra `query` usando a funcionalidade “Completar Palavra” do IntelliSense, pressione a **Guia**.

1. Finalize o bloco de código para que ele se pareça com o seguinte código. Você mesmo pode praticar usando os trechos de código novamente ao inserir `cw` e, então, pressionar a **Guia** duas vezes para gerar o código `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactoring-a-name"></a>Refatoração de um nome

Ninguém obtém o código correto na primeira vez e uma das coisas que talvez você queira alterar é o nome de uma variável ou de um método. Vamos experimentar a funcionalidade de [refatoração](../ide/refactoring-in-visual-studio.md) do Visual Studio para renomear a variável `_words` como `words`.

1. Coloque o cursor sobre a definição da variável `words` e selecione **Renomear...**  ao clicar com o botão direito do mouse ou no menu de contexto, ou pressione **Ctrl**+**R**, **Ctrl**+**R**.

   Uma caixa de diálogo pop-up chamada **Renomear** aparecerá no canto superior direito do editor.

1. Digite o nome desejado `words`. Observe que a referência ao `words` na consulta também será renomeada automaticamente. Antes de pressionar **Enter**, marque a caixa de seleção **Incluir Comentários** na caixa pop-up **Renomear**.

   ![Caixa de diálogo Renomear](media/quickstart-rename.png)

1. Pressione **ENTER**.

   As duas ocorrências de `words` foram renomeadas, bem como a referência ao `words` do comentário de código.

## <a name="next-steps"></a>Próximas etapas

Você concluiu este guia de início rápido para o editor do Visual Studio! Logo depois, você poderá testar alguns dos outros guias de início rápido para o IDE do Visual Studio. Veja mais maneiras de [navegar pelo código](../ide/navigating-code.md) ou confira os links para obter mais informações sobre os recursos que vimos. Caso contrário, boa codificação!

## <a name="see-also"></a>Consulte também

[Guia de início rápido: Introdução ao IDE do Visual Studio](../ide/quickstart-ide-orientation.md)  
[Guia de início rápido: Personalizar o Editor e o IDE do Visual Studio](../ide/quickstart-personalize-the-ide.md)  
[Guia de início rápido: Projetos e soluções](../ide/quickstart-projects-solutions.md)  
[Trechos de código](../ide/code-snippets.md)  
[Estrutura de tópicos](../ide/outlining.md)  
[Ir para Definição e Definição de Pico](../ide/go-to-and-peek-definition.md)  
[Refatoração](../ide/refactoring-in-visual-studio.md)  
[Usando o IntelliSense](../ide/using-intellisense.md)