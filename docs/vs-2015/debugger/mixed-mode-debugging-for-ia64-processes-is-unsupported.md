---
title: A depuração de modo misto para processos IA64 não é compatível. | Microsoft Docs
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
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3777ce079aea853400896408542380c5e2d16ef5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464462"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>A depuração de modo misto para processos IA64 não é compatível.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [depuração de modo misto para processos IA64 não há suporte.](https://docs.microsoft.com/visualstudio/debugger/mixed-mode-debugging-for-ia64-processes-is-unsupported).  
  
O Visual Studio não oferece suporte à depuração de modo misto de código gerenciado e nativo em processos IA64. Isso significa que, durante a depuração, você não pode depurar de código gerenciado para código nativo e vice-versa.  
  
### <a name="workarounds"></a>Soluções alternativas  
  
-   Depure seu código gerenciado e nativo em sessões separadas de depuração.  
  
     – ou –  
  
     Depure seu código misto como um processo de 32 bits, como descrito nos procedimentos a seguir.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Para alterar a plataforma para 32 bits (Visual Basic ou C#)  
  
1.  Na **Gerenciador de soluções**, clique com botão direito no projeto e clique **propriedades** no menu de atalho.  
  
2.  Nas páginas de propriedade, clique o **Compile** ou **depurar** guia.  
  
3.  Clique em **plataforma** e selecione x86 na lista de plataformas.  
  
     Por padrão, os compiladores padrão do Visual Basic e do C# produzem código para ser executado em qualquer CPU. Em um computador de 64 bits, esses binários são executados como processos de 64 bits. Para executar em um processo de 32 bits, você deve escolher **Win32**, e não **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Para alterar a plataforma para 32 bits (C/C++)  
  
1.  Na **Gerenciador de soluções**, clique com botão direito no projeto e clique **propriedades** no menu de atalho.  
  
2.  Nas páginas de propriedades, clique em **plataforma** e selecione Win32 na lista de plataformas,  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos de 64 bits](../debugger/debug-64-bit-applications.md)



