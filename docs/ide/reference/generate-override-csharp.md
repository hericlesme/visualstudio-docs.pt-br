---
title: "Gerar uma substituição - Geração de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3801d8ce60cf87126f8894bf44c77056f996cde1
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-an-override-in-c"></a>Gerar uma substituição em C# #

**O quê:** permite gerar imediatamente o código para qualquer método que possa ser substituído de uma classe base.

**Quando:** você quer substituir um método de classe base e gerar a assinatura automaticamente.

**Por quê:** você mesmo poderia escrever a assinatura do método, no entanto, esse recurso gerará automaticamente a assinatura.

**Como:**

1. digite a palavra-chave **override**, seguida por um espaço, no local onde você deseja inserir uma assinatura do método substituído, e uma lista suspensa de IntelliSense será exibida.

   ![IntelliSense de substituição](media/override-intellisense-cs.png)

1. Selecione o método que você deseja substituir a partir da classe base clicando nele com o mouse, ou navegando até ele com o teclado e pressionando **Enter**.

   >[!TIP]
   >* Use o ícone Propriedade ![Ícone de propriedade](media/override-property-cs.png) para mostrar ou ocultar as Propriedades na lista.
   >* Use o ícone de Método ![Ícone de método](media/override-method-cs.png) para mostrar ou ocultar os Métodos na lista.

1. A propriedade ou o método selecionado será adicionado à classe como uma substituição, pronta para ser implementada.

   ![Resultado da substituição](media/override-result-cs.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)
