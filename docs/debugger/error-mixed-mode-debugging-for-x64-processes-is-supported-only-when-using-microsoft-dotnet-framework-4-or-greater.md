---
title: "Erro: Modo misto depuração para processos x64 é suportada apenas ao usar o Microsoft .NET Framework 4 ou superior | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 87ca4ffe1a80d6d6fdc948c3a1617f888aba4baf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erro: depuração de modo misto para processos x64 só é suportada durante o uso do Microsoft .NET Framework 4 ou superior
Para depurar código nativo e gerenciado misto em um processo de 64 bits, você deverá ter a versão 4 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. A depuração de modo misto de processos de 64 bits com as versões do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anteriores à 4 não tem suporte.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Execute uma das seguintes etapas:  
  
    -   Atualize seu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para a versão 4.  
  
    -   Crie uma versão de 32 bits do aplicativo para depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)