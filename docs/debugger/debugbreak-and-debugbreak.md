---
title: DebugBreak e debugbreak | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1763c117ce9cdb815f12213830079136169b2c35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak e __debugbreak
Você pode chamar a função DebugBreak Win32 ou [debugbreak](/cpp/intrinsics/debugbreak) intrínseco em qualquer ponto no seu código. `DebugBreak` e `__debugbreak` têm o mesmo efeito de definir um ponto de interrupção nesse local.  
  
 Como `DebugBreak` é uma chamada para uma função do sistema, os símbolos de depuração do sistema devem ser instalados para garantir que as informações corretas da pilha de chamadas sejam exibidas depois de interromper. Caso contrário, as informações da pilha de chamadas exibidas pelo depurador podem estar desativadas por um quadro. Se você usar `__debugbreak`, os símbolos não serão necessários.  
  
## <a name="see-also"></a>Consulte também  
 [Intrínsecos do compilador](/cpp/intrinsics/compiler-intrinsics)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)   
 [Especifique o símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)