---
title: "Gerar uma substituição - geração de código (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d2972cfe2ea4481ab8f5eab6284277615d1d64a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-an-override-in-c"></a>Gerar uma substituição em c# #
**O que:** permite gerar imediatamente o código para um qualquer método que pode ser substituído de uma classe base. 

**Quando:** você deseja substituir um método de classe base e gerar a assinatura automaticamente.  

**Motivo:** você poderia escrever a assinatura do método, no entanto, esse recurso irá gerar automaticamente a assinatura. 

**Como:**

1. Tipo de **substituir** palavra-chave, seguido por um espaço onde você deseja inserir uma assinatura do método substituído e será exibida uma lista suspensa de IntelliSense.

   ![Substituir o IntelliSense](media/override_intellisense.png)

1. Selecione o método que você deseja substituir a classe base clicando nele com o mouse, ou navegando até o arquivo com o teclado e pressionando **Enter**.

   >[!TIP]
   >* Use o ícone de propriedade ![Ícone de propriedade](media/override_property.png) para mostrar ou ocultar propriedades na lista.
   >* Use o ícone de método ![Ícone de propriedade](media/override_method.png) para mostrar ou ocultar métodos na lista.

1. A propriedade ou método selecionado será adicionada à classe como uma substituição, pronta para ser implementada.

   ![Substituir os resultados](media/override_result.png)

## <a name="see-also"></a>Consulte também  
[Geração de código (C#)](../code-generation-csharp.md)  
