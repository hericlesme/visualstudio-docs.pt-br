---
title: "Gerar uma substituição de método no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: df0eecdeb2aad15e1da68cef3b125c3c95f57e78
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="generate-an-override-in-visual-studio"></a>Gerar uma substituição no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite gerar imediatamente o código para qualquer método que possa ser substituído de uma classe base.

**Quando:** você quer substituir um método de classe base e gerar a assinatura automaticamente.

**Por quê:** você mesmo poderia escrever a assinatura do método, no entanto, esse recurso gerará automaticamente a assinatura.

## <a name="how-to"></a>Como fazer

1. Digite `override` em C# ou `Overrides` em Visual Basic, seguido por um espaço, em que você deseja inserir um método de substituição.

   - C#:

    ![Substituição do IntelliSense em C#](media/override-intellisense-cs.png)

   - Visual Basic:

    ![Substituição do IntelliSense em VB](media/override-intellisense-vb.png)

1. Selecione o método que você deseja substituir da classe base.

   > [!TIP]
   > - Use o ícone de propriedade ![Ícone de propriedade](media/override-property-cs.png) para mostrar ou ocultar propriedades na lista.
   > - Use o ícone de método ![Ícone de método](media/override-method-cs.png) para mostrar ou ocultar métodos na lista.

   A propriedade ou o método selecionado será adicionado à classe como uma substituição, pronta para ser implementada.

   - C#:

      ![Resultado da substituição em C#](media/override-result-cs.png)

   - Visual Basic:

      ![Resultado da substituição em VB](media/override-result-vb.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)
