---
title: Como posso saber se meus ponteiros corrompem um endereço de memória? | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c9d3a6c754aa200703c5f2a0ed2e458e08830a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475127"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Como posso saber se meus ponteiros corrompem um endereço de memória?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como posso descobrir se Meus ponteiros corrompida um endereço de memória?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-find-out-if-my-pointers-corrupt-a-memory-address-q).  
  
Descrição do problema  
 Eu acho que um de meus ponteiros pode estar danificando a memória no endereço 0x00408000. Como posso descobrir o que está acontecendo lá?  
  
## <a name="solution"></a>Solução  
  
#### <a name="check-for-heap-corruption"></a>Verificação de danos do heap  
  
-   A maior parte das corrupções de memória acontece, na verdade, devido à corrupção da heap. Tente usar o utilitário global dos sinalizadores (gflags.exe) ou pageheap.exe. Ver [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Para localizar onde o endereço de memória foi alterado  
  
1.  Defina um ponto de interrupção de dados em 0x00408000. Ver [definir um ponto de interrupção de alteração de dados (somente C++ nativo)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Quando você atinge o ponto de interrupção, use o **memória** de conteúdo da janela para exibir a memória que começam em 0x00408000. Para obter mais informações, consulte [memória Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes do código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)



