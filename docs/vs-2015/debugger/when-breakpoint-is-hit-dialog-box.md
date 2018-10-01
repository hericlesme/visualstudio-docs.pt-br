---
title: Quando o ponto de interrupção é a caixa de diálogo ocorrências | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 650e390abde6f3ad99e5a0c30591c8d1530df692
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465560"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Caixa de diálogo Ponto de Interrupção Quando Visitado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [ao ponto de interrupção é atingido caixa de diálogo](https://docs.microsoft.com/visualstudio/debugger/when-breakpoint-is-hit-dialog-box).  
  
Com essa caixa de diálogo, você pode personalizar a ação que ocorre quando um ponto de interrupção é atingido.  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Imprimir uma mensagem**  
 Imprime uma mensagem, usando a sintaxe do DebuggerDisplay. Para obter mais informações, consulte [usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Essa caixa de texto também oferece suporte à palavras-chave especiais (como $ADDRESS) que podem ser usadas por si mesmas ou nas chaves de uma expressão do DebuggerDisplay. As palavras-chave disponíveis são listadas na caixa de diálogo.  
  
 **Continuar execução**  
 Esse controle será habilitado somente quando **imprimir uma mensagem** está selecionado. Com esse controle selecionado, você pode usar um ponto de interrupção como um tracepoint para rastrear a execução do programa, em vez de interrompê-lo quando o local for atingido.  
  
## <a name="see-also"></a>Consulte também  
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)   
 [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)



