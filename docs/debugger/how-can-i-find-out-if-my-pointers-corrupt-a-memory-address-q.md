---
title: Como posso saber se meus ponteiros corrompem um endereço de memória? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8965ec268e5d236b9a33e5c3e8acfa35e51dcdb3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479306"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Como posso saber se meus ponteiros corrompem um endereço de memória?
## <a name="problem-description"></a>Descrição do problema  
 Eu acho que um de meus ponteiros pode estar danificando a memória no endereço 0x00408000. Como posso descobrir o que está acontecendo lá?  
  
## <a name="solution"></a>Solução  
  
#### <a name="check-for-heap-corruption"></a>Verificação de danos do heap  
  
-   A maior parte das corrupções de memória acontece, na verdade, devido à corrupção da heap. Tente usar o utilitário global dos sinalizadores (gflags.exe) ou pageheap.exe. Consulte [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Para localizar onde o endereço de memória foi alterado  
  
1.  Defina um ponto de interrupção de dados em 0x00408000. Consulte [definir um ponto de interrupção de alteração de dados (apenas C++ nativo)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Quando você atinge o ponto de interrupção, use o **memória** começando em 0x00408000 de conteúdo da janela para visualizar a memória. Para obter mais informações, consulte [memória Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes de código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)