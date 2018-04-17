---
title: Como usar trechos de código XML no Microsoft Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5751293124edab5c8415cd60d79aba9947fb94bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-xml-snippets"></a>Como: usar XML trechos de código

Você pode chamar trechos XML usando os dois seguintes comandos no menu de atalho do editor XML. O **Inserir trecho** comando insere o trecho XML na posição do cursor. O **Surround With** comando encapsula o trecho de código XML ao redor do texto selecionado. Cada pequena notícias XML designou tipos de notícias pequena. Os tipos de trecho determinam se o trecho de código está disponível com o **Inserir trecho** comando, o **Surround With** comando, ou ambos.

Depois que o trecho XML foi adicionado ao editor, todos os campos editáveis no trecho estão realçados em amarelo, e o cursor está localizado no primeiro campo editável.

## <a name="insert-snippet"></a>Inserir o trecho de código

Os procedimentos a seguir descrevem como acessar o **Inserir trecho** comando.

> [!NOTE]
> O **Inserir trecho** comando também está disponível por meio do atalho de teclado (**Ctrl**+**K**, em seguida, **Ctrl** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Para inserir trechos do menu de atalho

1. Posicionar o cursor onde você deseja inserir o trecho XML.

2. Clique com botão direito e selecione **Inserir trecho**.

   Uma lista de trechos disponíveis XML é exibida.

3. Selecione um trecho da lista usando o mouse ou digitando o nome do trecho de código e pressionando **guia** ou **Enter**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Para inserir trechos usando o menu do IntelliSense

1. Posicionar o cursor onde você deseja inserir o trecho XML.

2. Do **editar** , aponte para **IntelliSense**e, em seguida, selecione **Inserir trecho**.

   Uma lista de trechos disponíveis XML é exibida.

3. Selecione um trecho da lista usando o mouse ou digitando o nome do trecho de código e pressionando **guia** ou **Enter**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Para inserir trechos com o IntelliSense concluir a lista de palavras

1. Posicionar o cursor onde você deseja inserir o trecho XML.

2. Comece a digitar o trecho XML que você deseja adicionar ao seu arquivo. Se o preenchimento automático é ativada, a lista de palavras completo do IntelliSense é exibida. Se não aparecer, pressione **Ctrl**+**espaço** para ativá-lo.

3. Selecione o trecho XML da lista de palavras completo.

4. Pressione **guia**, **guia** para invocar o trecho XML.

> [!NOTE]
> Pode haver casos quando o trecho XML não é chamado. Por exemplo, se você tentar inserir um elemento de `xs:complexType` dentro de um nó de `xs:element` , o editor não gerencia um trecho XML. Quando um elemento de `xs:complexType` é usado dentro de um nó de `xs:element` , não houver nenhum atributo ou subelements necessário, o editor não tem nenhum dados para inserir.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Para inserir trechos usando o nome do atalho

1. Posicionar o cursor onde você deseja inserir o trecho XML.

2. Tipo `<` no painel do editor.

3. Pressione **Esc** para fechar a lista de palavras de conclusão do IntelliSense.

4. Digite o nome do atalho do trecho e pressione **guia** para invocar o trecho XML.

## <a name="surround-with"></a>Envolver com

Os procedimentos a seguir descrevem como acessar o **Surround With** comando.

> [!NOTE]
> O **Surround With** comando também está disponível por meio do atalho de teclado (**Ctrl**+**K**, em seguida, **Ctrl** + **S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Para usar a bordadura com o menu de contexto

1. Selecione o texto para colocar no editor XML.

2. Clique com botão direito e selecione **Surround With**.

   Uma lista de bordadura disponíveis com trechos XML é exibida.

3. Selecione um trecho da lista usando o mouse ou digitando o nome do trecho de código e pressionando **guia** ou **Enter**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Para usar surround com o menu do IntelliSense

1. Selecione o texto para colocar no editor XML.

2. Do **editar** , aponte para **IntelliSense**e, em seguida, selecione **Surround With**.

   Uma lista de bordadura disponíveis com trechos XML é exibida.

3. Selecione um trecho da lista usando o mouse ou digitando o nome do trecho de código e pressionando **guia** ou **Enter**.

## <a name="using-xml-snippets"></a>Usando trechos XML

Uma vez que você escolher um trecho XML, o texto de trecho de código é inserido automaticamente a posição do cursor. Todos os campos editáveis no trecho são realçadas, e o primeiro campo editável é automaticamente selecionado. O campo selecionado é convertido.

Quando um campo é selecionado, você pode digitar um novo valor para o campo. Pressionar **guia** alterna entre os campos editáveis do trecho de código; pressionando **Shift**+**guia** percorre-los na ordem inversa. Clicando em um campo colocar o cursor no campo, e clique duas vezes em um campo selecioná-lo. Quando um campo é realçado, uma dica de ferramenta pode ser exibido, oferecendo uma descrição do campo.

Somente a primeira instância de um campo dado é editável. Quando esse campo é realçado, as outras instâncias do campo são descritas. Quando você altera o valor de um campo editável, o campo ele alterado everywhere é usado no trecho.

Pressionar **Enter** ou **Esc** cancela a edição de campos e retorna o editor normal.

As cores padrão para campos do trecho de código editável podem ser alteradas modificando a configuração de campo de trecho de código no **fontes e cores** painel do **opções** caixa de diálogo. Para obter mais informações, consulte [como: alterar fontes e cores no Editor de](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Consulte também

- [Trechos de código XML](../xml-tools/xml-snippets.md)
- [Como gerenciar um trecho de código de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Como criar trechos de código XML](../xml-tools/how-to-create-xml-snippets.md)