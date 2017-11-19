---
title: 'Como: usar Editar e continuar (c#) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec66bd21eb119c348391f191f23570e66119122f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-edit-and-continue-c"></a>Como usar Editar e Continuar (C#)
Com a função Editar e Continuar no C#, é possível fazer alterações em seu código no modo de interrupção durante a depuração. As alterações podem ser aplicadas sem precisar interromper e reiniciar a sessão de depuração.  
  
 Editar e continuar é invocado automaticamente quando você fazer alterações no modo de interrupção e escolha uma execução do depurador, como comando **continuar**, **etapa**, ou **definir próxima instrução**, ou avaliar uma função em uma janela de depurador.  
  
> [!NOTE]
>  Não há suporte para editar e continuar quando a depuração de otimização de código, o código nativo/gerenciado misto ou o código de integração do SQL Server common language runtime (CLR). Para obter informações sobre outros cenários sem suporte, consulte [suporte para alterações de código (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md). Se você tentar aplicar alterações de código em um desses cenários, as exibições de depurador uma explicação de caixa diálogo que editar e continuar não tem suporte.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Para invocar a função Editar e Continuar automaticamente  
  
1.  No modo de interrupção, faça uma alteração no código-fonte.  
  
2.  Do **depurar** menu, clique em **continuar**, **etapa**, ou **definir próxima instrução** ou avaliar uma função em uma janela de depurador.  
  
     O novo código é compilado e a depuração continua com o novo código. Algumas alterações não têm suporte para a função Editar e Continuar. Para obter mais informações, consulte [suporte para alterações de código (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar/desabilitar a função Editar e Continuar  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  No **opções** caixa de diálogo caixa, expanda o **depuração** nó e selecione **editar e continuar**.  
  
3.  No **opções** caixa de diálogo **editar e continuar** página, marque ou desmarque o **habilitar editar e continuar** caixa de seleção.  
  
     A configuração entra em vigor quando você reinicia a sessão de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Editar e continuar (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Alterações de código suportadas (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md)   