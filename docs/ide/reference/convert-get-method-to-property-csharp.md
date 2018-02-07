---
title: "Converter o método Get em propriedade e converter uma propriedade em um método Get no C# | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: a23af31c5099908ed0b6fed07404216a57975f75
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Converter o método Get em propriedade/Converter propriedade em um método Get

## <a name="convert-get-method-to-property"></a>Converter o método Get em propriedade

**O quê:** permite converter um método Get em uma propriedade (e opcionalmente seu método Set) e vice-versa.

**Quando:** você tem um método Get que não contêm nenhuma lógica.

**Como:**

1. coloque o cursor no nome do seu método Get.

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Substituir método pela propriedade** no pop-up da janela Visualização. Se você tiver um método Set, também pode converter seu método Set neste momento selecionando **Substituir método Get e método Set pela propriedade**.
   * **Mouse**
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Substituir método pela propriedade** no pop-up da janela Visualização. Se você tiver um método Set, também pode converter seu método Set neste momento selecionando **Substituir método Get e método Set pela propriedade**.

1. Se você estiver satisfeito com a alteração na visualização do código, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

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

## <a name="convert-property-to-get-method"></a>Converter propriedade em método Get

**O quê:** permite converter uma propriedade em um método Get

**Quando:** você tem uma propriedade que envolve mais do que imediatamente configurar e obter um valor 

**Como:**

1. coloque o cursor no nome do seu método Get.

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Substituir propriedade por métodos** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Substituir propriedade por métodos** no pop-up da janela Visualização.

1. Se você estiver satisfeito com a alteração na visualização do código, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)