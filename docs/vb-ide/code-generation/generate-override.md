---
title: "Gerar uma substituição - geração de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4a384eb3e75a499eb2a35c747f003846580738e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="generate-an-override-in-visual-basic"></a>Gerar uma substituição no Visual Basic
**O que:** permite gerar imediatamente o código para um qualquer método que pode ser substituído de uma classe base. 

**Quando:** você deseja substituir um método de classe base e gerar a assinatura automaticamente.  

**Motivo:** você poderia escrever a assinatura do método, no entanto, esse recurso irá gerar automaticamente a assinatura. 

**Como:**

1. Tipo de **substitui** palavra-chave, seguido por um espaço onde você deseja inserir uma assinatura do método substituído e será exibida uma lista suspensa de IntelliSense.

   ![Substituir o IntelliSense](media/override_intellisense.png)

1. Selecione o método que você deseja substituir a classe base clicando nele com o mouse, ou navegando até o arquivo com o teclado e pressionando **Enter**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override_property.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override_method.png) to show or hide Methods in the list.
-->

1. A propriedade ou método selecionado será adicionada à classe como uma substituição, pronta para ser implementada.

   ![Substituir os resultados](media/override_result.png)

## <a name="see-also"></a>Consulte também  
[Geração de código (Visual Basic)](../code-generation-vb.md) 