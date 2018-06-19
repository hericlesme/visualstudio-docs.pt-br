---
title: Opções, Editor de Texto, C#, IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d8f6928dd09b971e2c5924d34058a1a0d5e28394
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947385"
---
# <a name="options-text-editor-c-intellisense"></a>Opções, Editor de Texto, C#, IntelliSense

Use a página de opções **IntelliSense** para modificar as configurações que afetam o comportamento do IntelliSense para C#. Para acessar essa página de opções, escolha **Ferramentas** > **Opções** e, em seguida, **Editor de Texto** > **C#** > **IntelliSense**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

As opções do **IntelliSense** contém as seguintes seções:

## <a name="completion-lists"></a>Listas de Conclusão

- Mostrar lista de conclusão depois que um caractere for digitado*

   Quando essa opção estiver selecionada, o IntelliSense exibirá automaticamente a lista de preenchimento quando você começar a digitar. Quando essa opção não estiver selecionada, o preenchimento do IntelliSense ainda estará disponível no menu **IntelliSense** ou pressionando **Ctrl**+**Espaço**.

- Mostrar lista de conclusão depois que um caractere for excluído

- Realçar partes correspondentes de itens da lista de conclusão

- Mostrar filtros da lista de conclusão

- Mostrar sugestões de nome

### <a name="snippets-behavior"></a>Comportamento de trechos de código

- Nunca incluir trechos de código

   Quando essa opção estiver selecionada, o IntelliSense nunca adicionará aliases de trechos de código C# à lista de conclusão.

- Sempre incluir trechos de código

   Quando essa opção estiver selecionada, o IntelliSense adicionará aliases de trechos de código C# à lista de preenchimento. Caso o alias do trecho de código seja igual a uma palavra-chave, por exemplo, [classe](/dotnet/csharp/language-reference/keywords/class), a palavra-chave será substituída pelo atalho. Para saber mais, consulte [Trechos de código C#](../../ide/visual-csharp-code-snippets.md).

- Incluir trechos quando ?-Tab for digitado após um identificador

   Quando essa opção estiver selecionada, o IntelliSense adicionará aliases de trechos de código C# à lista de conclusão quando **?**+**Tab** for pressionado após um identificador

### <a name="enter-key-behavior"></a>Comportamento da tecla Enter

- Nunca adicionar uma nova linha ao pressionar Enter

   Especifica que uma nova linha nunca será adicionada automaticamente depois de selecionar um item na lista de conclusão e pressionar **Enter**.

- Apenas adicionar uma nova linha ao pressionar Enter após o final de uma palavra totalmente digitada

   Especifica que, se você digitar todos os caracteres de uma entrada na lista de conclusão e, em seguida, pressionar **Enter**, uma nova linha será adicionada automaticamente e o cursor será movido para a nova linha.

   Por exemplo, se você digitar `else` e, em seguida, pressionar **Enter**, o seguinte será exibido no editor:

   `else`

   `|` (local do cursor)

   No entanto, se você digitar apenas `el` e, em seguida, pressionar **Enter**, o seguinte será exibido no editor:

   `else|` (local do cursor)

- Sempre adicionar uma nova linha ao pressionar Enter

   Especifica que, se você digitar *qualquer* um dos caracteres de uma entrada na lista de conclusão e depois pressionar **Enter**, uma nova linha será adicionada automaticamente e o cursor passará para a nova linha.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
- [Usando o IntelliSense](../../ide/using-intellisense.md)