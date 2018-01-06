---
title: "Converter o método Get para a propriedade - refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 71ff3db81be256bdb82413d04b2f939b706c6586
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Converter o método Get de propriedade / converter a propriedade para o método Get
## <a name="convert-get-method-to-property"></a>Converter o método Get de propriedade
**O que:** lhe permite converter um método Get em uma propriedade (e, opcionalmente, o método de conjunto) e vice-versa.

**Quando:** tem um método Get que não contêm nenhuma lógica.

**Como:**

1. Coloque o cursor em seu nome do método Get.

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **substituir o método com a propriedade** do popup da janela de visualização. Se você tiver um método definido, você também pode converter seu método de conjunto neste momento selecionando **método substituir Get e método de conjunto com a propriedade**.
   * **Mouse**
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **substituir o método com a propriedade** do popup da janela de visualização. Se você tiver um método definido, você também pode converter seu método de conjunto neste momento selecionando **método substituir Get e método de conjunto com a propriedade**.

1. Se você estiver satisfeito com a alteração na visualização de código, pressione **Enter** ou clique na correção do menu e as alterações serão confirmadas.

Exemplo:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Converter a propriedade para o método Get
**O que:** permite converter uma propriedade de um método Get

**Quando:** tem uma propriedade que envolve a configuração de mais de imediatamente e obter um valor 

**Como:**

1. Coloque o cursor em seu nome do método Get.

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **substituir a propriedade com métodos** do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **substituir a propriedade com métodos** do popup da janela de visualização.

1. Se você estiver satisfeito com a alteração na visualização de código, pressione **Enter** ou clique na correção do menu e as alterações serão confirmadas.

## <a name="see-also"></a>Consulte também  
[Refatoração (C#)](../refactoring-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)