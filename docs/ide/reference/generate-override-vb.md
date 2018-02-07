---
title: "Gerar uma substituição - Geração de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
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
- multiple
ms.openlocfilehash: 334f5a79dad1b7d2c14768d0698797a34ad039c5
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-an-override-in-visual-basic"></a>Gerar uma substituição em Visual Basic
**O quê:** permite gerar imediatamente o código para qualquer método que possa ser substituído de uma classe base. 

**Quando:** você quer substituir um método de classe base e gerar a assinatura automaticamente.  

**Por quê:** você mesmo poderia escrever a assinatura do método, no entanto, esse recurso gerará automaticamente a assinatura. 

**Como:**

1. digite a palavra-chave **Overrides**, seguida por um espaço, no local onde você deseja inserir uma assinatura do método substituído, e uma lista suspensa de IntelliSense será exibida.

   ![IntelliSense de substituição](media/override-intellisense-vb.png)

1. Selecione o método que você deseja substituir a partir da classe base clicando nele com o mouse, ou navegando até ele com o teclado e pressionando **Enter**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override-property-vb.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override-method-vb.png) to show or hide Methods in the list.
-->

1. A propriedade ou o método selecionado será adicionado à classe como uma substituição, pronta para ser implementada.

   ![Resultado da substituição](media/override-result-vb.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md) 