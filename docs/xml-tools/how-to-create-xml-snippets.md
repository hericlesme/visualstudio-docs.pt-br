---
title: 'Como: Crie trechos XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae09c578eac5a4acbfa9c169ba175fe557872da5
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548538"
---
# <a name="how-to-create-xml-snippets"></a>Como: Crie trechos XML

O editor XML pode ser usado para criar novos trechos XML. O editor inclui um trecho XML, chamado “pequena notícias”, que é uma pequena notícias de texto constante para criar novos trechos XML.

## <a name="to-create-a-new-xml-snippet"></a>Para criar um novo trecho XML

 Para criar um novo código XML, o trecho de código cria um novo arquivo XML e usar o **Inserir trecho** recurso.

1.  Sobre o **arquivo** menu, clique em **novo** e, em seguida, clique em **arquivo**.

2.  Clique em **arquivo XML** e, em seguida, clique em **abrir**.

3.  No painel do editor e selecione **Inserir trecho**.

4.  Selecione **trecho** na lista e pressione **Enter**.

5.  Faça as alterações para o novo trecho.

6.  Do **arquivo** menu, selecione **salvar XMLFile**.

     O **salvar arquivo como** caixa de diálogo é exibida.

7.  Insira o nome para o novo trecho de código e selecione **arquivos de trecho** do **Salvar como tipo** janela suspensa.

8.  Use o **salvar em** lista suspensa para alterar o local do arquivo para o *Meus Documentos\Visual Studio 2005\Code Snippets\XML\My XML trechos* pasta e depois pressione **salvar**.

## <a name="snippet-description"></a>Descrição do trecho de código

 Esta seção descreve alguns dos elementos-chave no trecho de texto constante. Para obter mais informações sobre os elementos do esquema usado pelos trechos de código XML, consulte [referência de esquema de trechos de código](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>Elemento SnippetType

 Suporte do editor dois tipos de trecho:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

 O `Expansion` tipo determina se o trecho de código aparece quando você invoca o **Inserir trecho** comando. O `SurroundsWith` tipo determina se o trecho de código aparece quando você invoca o **Surrounds com** comando.

### <a name="code-element"></a>Elemento de código

 O elemento de `Code` define o texto XML que será inserido quando o trecho é chamado.

> [!NOTE]
> O texto de trecho XML deve ser incluído em uma seção de `<![CDATA[...]]>` .


 O seguinte é o elemento de `Code` que é criado pelo trecho de texto constante.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

 O elemento de `Code` inclui três variáveis.

-   $name$ variável é definido pelo usuário. Cria um elemento de `name` , que tem um valor editável que usa padrão “para nomear”. As variáveis definidas pelo usuário são definidos usando o elemento de `Literal` .

-   $selected$ é uma variável predefinido. Representa o texto que foi selecionado no editor XML antes de chamar o trecho. O posicionamento dessa variável determina onde o texto selecionado aparece no trecho de código que circunda a seleção.

-   $end$ é uma variável predefinido. Quando o usuário pressiona **Enter** para terminar de editar os campos do trecho de código, essa variável determina onde o acento circunflexo (^) é movido.

 O elemento acima de `Code` insira o seguinte texto XML:

```xml
<test>
  <name>name</name>
</test>
```

 O valor do elemento de nome é marcado como uma região editável.

### <a name="literal-element"></a>Elemento literal

 O elemento de `Literal` é usado para identificar o texto de substituição que pode ser personalizada depois que é inserido no arquivo. Por exemplo, cadeias de caracteres literais, os valores numéricos, e alguns nomes de variável podem ser declarados como literais. Você pode definir qualquer número do trecho em literais XML e você pode referir-lhes várias vezes dentro de trecho. O código a seguir é um exemplo de um elemento de `Literal` que define um variável de $name$ cujo valor padrão é “nome”.

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

 Literais também podem se referir funções. O Editor de XML inclui uma função chamada **LookupPrefix**. O **LookupPrefix** função procura o URI do namespace especificado no local no documento XML que este trecho de código é invocado do e retorna o prefixo de namespace que é definido para esse namespace, se houver, e inclui os dois-pontos (:) Esse nome. A seguir está um exemplo de um `Literal` elemento que usa o **LookupPrefix** função.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

 A variável de $prefix$ pode então ser usado em qualquer lugar no seu trecho XML.

## <a name="see-also"></a>Consulte também

- [Trechos XML](../xml-tools/xml-snippets.md)
- [Como: usar XML trechos de código](../xml-tools/how-to-use-xml-snippets.md)
- [Como: gerar um fragmento de XML de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)