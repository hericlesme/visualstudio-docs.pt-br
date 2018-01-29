---
title: "Trechos de Código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e2b973b00e132973b8569bc5cad8c1f1318317cd
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="code-snippets"></a>Trechos de código

Trechos de código são pequenos blocos de código reutilizável que podem ser inseridos em um arquivo de código usando um comando de menu de contexto ou uma combinação de teclas de atalho. Eles geralmente contêm blocos de código comumente usados como try-finally ou blocos if-else, mas podem ser usados para inserir métodos ou classes inteiros.

## <a name="expansion-snippets-and-surround-with-snippets"></a>Trechos de expansão e trechos Surround-With

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

Você pode inserir esse trecho clicando em **Inserir Trecho** no menu de contexto da janela de código, depois em **Visual C#** e, então digite `tryf` e, em seguida, pressione a **Guia** ou você pode digitar `tryf` e pressionar a **Guia** duas vezes.

Um exemplo de um trecho “envolver com”: em C++, o atalho `if` pode ser usado como um trecho de inserção ou um trecho “envolver com”. Se você selecionar uma linha de código (por exemplo, `return FALSE;`) e, em seguida, clicar em **Envolver com** e então em **se**, o trecho de código será expandido ao redor da linha:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parâmetros de substituição de trecho

Trechos podem conter parâmetros de substituição, que são espaços reservados que você deve substituir de acordo com o código exato que você está escrevendo. No exemplo anterior, `true` é um parâmetro de substituição, que você poderia substituir pela condição apropriada. A substituição feita é repetida para cada instância do mesmo parâmetro de substituição no trecho.

Por exemplo, no Visual Basic, há um trecho de código que insere uma propriedade. Clique em **Inserir Trecho** no menu de contexto da janela de código, então em **Padrões de Código**, **Propriedades, Procedimentos, Eventos** e, em seguida, escolha Definir uma propriedade. O código a seguir é inserido:

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

## <a name="code-snippet-manager"></a>Gerenciador de trecho de código

Você pode ver todos os trechos de código que estão instalados no momento, além de sua localização no disco, selecionando **Ferramentas**, **Gerenciador de Trecho de Código**. Trechos são exibidos por idioma.

Você pode adicionar e remover diretórios de trecho com os botões **Adicionar** e **Remover** na caixa de diálogo **Gerenciador de Trechos de Código**. Para adicionar trechos de código individuais, use o botão **Importar**.

## <a name="see-also"></a>Consulte também

[Passo a passo: criando um trecho de código](../ide/walkthrough-creating-a-code-snippet.md)  
[Como distribuir trechos de código](../ide/how-to-distribute-code-snippets.md)  
[Melhores práticas para usar trechos de código](../ide/best-practices-for-using-code-snippets.md)  
[Solução de problemas de trechos](../ide/troubleshooting-snippets.md)  
[Trechos de código do Visual C#](../ide/visual-csharp-code-snippets.md)  
[Trechos de código do Visual C++](../ide/visual-cpp-code-snippets.md)  
[Referência de esquema dos trechos de código](../ide/code-snippets-schema-reference.md)