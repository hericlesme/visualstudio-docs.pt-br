---
title: DebugBreak e debugbreak | Microsoft Docs
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
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 005490038b293dbb644ec99ca2fbeaa77c0eb2c9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474935"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak e __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [DebugBreak e debugbreak](https://docs.microsoft.com/visualstudio/debugger/debugbreak-and-debugbreak).  
  
Você pode chamar a função DebugBreak Win32 ou o [debugbreak](http://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) intrínseca em qualquer ponto no seu código. `DebugBreak` e `__debugbreak` têm o mesmo efeito de definir um ponto de interrupção nesse local.  
  
 Como `DebugBreak` é uma chamada para uma função do sistema, os símbolos de depuração do sistema devem ser instalados para garantir que as informações corretas da pilha de chamadas sejam exibidas depois de interromper. Caso contrário, as informações da pilha de chamadas exibidas pelo depurador podem estar desativadas por um quadro. Se você usar `__debugbreak`, os símbolos não serão necessários.  
  
## <a name="see-also"></a>Consulte também  
 [Intrínsecos do compilador](http://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)   
 [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



