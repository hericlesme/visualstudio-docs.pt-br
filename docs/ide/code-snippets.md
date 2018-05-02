---
title: Trechos de código
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: a054ba07596135b08260ded028f07701fce9196d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="code-snippets"></a>Trechos de código

Trechos de código são pequenos blocos de código reutilizável que podem ser inseridos em um arquivo de código usando um comando de menu de contexto ou uma combinação de teclas de atalho. Eles geralmente contêm os blocos de código mais usados, como `try-finally` ou `if-else`, mas podem ser usados para inserir métodos ou classes inteiras.

Os trechos de código estão disponíveis para uma variedade de linguagens, incluindo C#, C++, Visual Basic, XML e T-SQL, entre outras. Para exibir todos os trechos instalados disponíveis para uma linguagem, abra o **Gerenciador de Trechos de Código** no menu **Ferramentas** do Visual Studio e escolha a linguagem no menu suspenso na parte superior.

![Caixa de diálogo Gerenciador de Trechos de Código](media/code-snippets-manager.png)

Em geral, os trechos de código podem ser acessados das seguintes maneiras:

- Na barra de menus, escolha **Editar** > **IntelliSense** > **Inserir Trecho de Código...**

- No menu acionado com o botão direito do mouse ou menu de contexto, do editor de códigos, escolha **Trecho de Código** > **Inserir Trecho de Código...**

- Usando o teclado, pressione **Ctrl**+**K**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Trechos de expansão e trechos de “envolver com”

Há dois tipos de trecho de código no Visual Studio: trechos de expansão, que são adicionados a um ponto de inserção especificado e podem substituir um atalho de trecho; e trechos Surround-with (somente C# e C++), que são adicionados ao redor de um bloco de código selecionado.

Um exemplo de um trecho de expansão: em C#, o atalho tryf é usado para inserir um bloco try-finally:

```csharp
try
{

}
finally
{

}
```

Você pode inserir esse trecho de código clicando em **Inserir Trecho de Código** no menu de contexto da janela de código, em seguida, clicando em **Visual C#**, digitando `tryf` e pressionando **Tab**. Ou, você pode digitar `tryf` e pressionar **Tab** duas vezes.

Um exemplo de um trecho “envolver com”: em C++, o atalho `if` pode ser usado como um trecho de inserção ou um trecho “envolver com”. Se você selecionar uma linha de código (por exemplo `return FALSE;`) e, em seguida, escolher **Envolver Com** > **if**, o trecho de código será expandido na linha:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parâmetros de substituição de trecho de código

Trechos podem conter parâmetros de substituição, que são espaços reservados que você deve substituir de acordo com o código exato que você está escrevendo. No exemplo anterior, `true` é um parâmetro de substituição, que você poderia substituir pela condição apropriada. A substituição feita é repetida para cada instância do mesmo parâmetro de substituição no trecho.

Por exemplo, no Visual Basic, há um trecho de código que insere uma propriedade. Para inserir o trecho de código, escolha **Trecho de Código...**  > **Inserir Trecho de Código** no menu acionado com o botão direito do mouse ou menu de contexto, em um arquivo de código em Visual Basic. Em seguida, escolha **Padrões de Código** > **Propriedades, Procedimentos, Eventos** > **Definir uma Propriedade**.

![Menu de trecho de código para Definir uma propriedade](media/code-snippets-vb-property.png)

O código a seguir é inserido:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Se você alterar `newPropertyValue` para `m_property`, cada instância de `newPropertyValue` será alterada. Se você alterar `String` para `Int` na declaração de propriedade, o valor no método conjunto também mudará para `Int`.

## <a name="see-also"></a>Consulte também

- [Instruções passo a passo: criando um trecho de código](../ide/walkthrough-creating-a-code-snippet.md)
- [Como distribuir trechos de código](../ide/how-to-distribute-code-snippets.md)
- [Melhores práticas para usar trechos de código](../ide/best-practices-for-using-code-snippets.md)
- [Solução de problemas de trechos](../ide/troubleshooting-snippets.md)
- [Trechos de código C#](../ide/visual-csharp-code-snippets.md)
- [Trechos de código do Visual C++](../ide/visual-cpp-code-snippets.md)
- [Referência de esquema dos trechos de código](../ide/code-snippets-schema-reference.md)