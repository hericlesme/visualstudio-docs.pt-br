---
title: Refatorar código para converter um loop for em uma instrução foreach
ms.date: 05/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refatoração para converter entre um loop for e uma instrução foreach

Essas refatorações aplicam-se a:

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Converter um loop for em uma instrução foreach

Se você tiver um loop [for](/dotnet/csharp/language-reference/keywords/for) em seu código, será possível usar essa refatoração para convertê-lo em uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

### <a name="why-convert"></a>Por que converter

Os motivos pelos quais talvez você deseje converter um loop [for](/dotnet/csharp/language-reference/keywords/for) em uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) incluem:

- Você não usa a variável de contagem de iterações dentro do loop, exceto com um índice para acessar o item.

- Você deseja simplificar seu código e reduza a probabilidade de erros lógicos nas instruções do inicializador, de condição e de iteração.

### <a name="how-to-use-it"></a>Como usá-lo

1. Coloque o cursor na primeira linha do loop `for`.

1. Pressione **Ctrl**+**.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Converter em menu foreach](media/convert-to-foreach.png)

1. Selecione **Converter em 'foreach'**. Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Converter uma instrução foreach em um loop for

Se você tiver uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) em seu código, use essa refatoração para convertê-lo em um loop [for](/dotnet/csharp/language-reference/keywords/for).

### <a name="why-convert"></a>Por que converter

Os motivos pelos quais talvez você deseje converter uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) em um loop [for](/dotnet/csharp/language-reference/keywords/for) incluem:

- Você deseja usar a variável de contagem de iterações dentro do loop para outras funções além de apenas acessar o item.

- Você está [iterando por meio de uma matriz multidimensional](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) e deseja ter mais controle sobre os elementos da matriz.

### <a name="how-to-use-it"></a>Como usá-lo

1. Coloque o cursor na primeira linha da instrução `foreach`.

1. Pressione **Ctrl**+**.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Converter em menu for](media/convert-to-for.png)

1. Selecione **Converter em 'for'**. Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

1. Como a refatoração introduz uma nova variável de contagem de iterações, a caixa **Renomear** é exibida no canto superior direito do editor. Se desejar escolher um nome diferente para a variável, digite-o e, em seguida, pressione **Enter** ou selecione **Aplicar** na caixa **Renomear**. Se você não deseja escolher um novo nome, pressione **Esc** ou selecione **Aplicar** para ignorar a caixa **Renomear**.

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)