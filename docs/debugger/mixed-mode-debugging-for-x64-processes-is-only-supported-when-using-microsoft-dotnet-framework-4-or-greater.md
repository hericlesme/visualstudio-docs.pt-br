---
title: Modo misto de depuração para x64 processos só tem suporte ao usar o Microsoft.NET Framework 4 ou superior | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ceb332fab5e09fa4aaf57d3a89e20270643b705
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475165"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>A depuração do modo misto para processos x64 só é suportada durante o uso do Microsoft.NET Framework 4 ou superior
As versões do .NET Framework anteriores à versão 4 não fornecem suporte à depuração de modo misto de processos do x64. Isso significa que você não pode depurar de código gerenciado para código nativo, ou do código nativo para o código gerenciado.  
  
### <a name="workarounds"></a>Soluções alternativas  
  
-   Atualize seu projeto para usar o Microsoft .NET Framework 4 ou posterior.  
  
     -ou-  
  
     Depure seu código gerenciado e nativo em sessões separadas de depuração.  
  
     -ou-  
  
     Depure seu código misto como um processo de 32 bits, como descrito nos procedimentos a seguir.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Para alterar a plataforma para 32 bits (Visual Basic ou C#)  
  
1.  Em **Solution Explorer**, clique com o botão direito e, em seguida, clique em **propriedades**.  
  
2.  Nas páginas de propriedades, clique no **compilar** ou **depurar** guia.  
  
3.  Clique em **plataforma** e selecione na lista de plataformas x86.  
  
     Por padrão, os compiladores padrão do Visual Basic e do C# produzem código para ser executado em qualquer CPU. Em um computador de 64 bits, esses binários são executados como processos de 64 bits. Para executar em um processo de 32 bits, você deve escolher **Win32**, não **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Para alterar a plataforma para 32 bits (C/C++)  
  
1.  Em **Solution Explorer**, clique com o botão direito e clique em **propriedades**.  
  
2.  Nas páginas de propriedades, clique em **plataforma** e selecione na lista de plataformas Win32.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Consulte [Configurando a depuração SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos de 64 bits](../debugger/debug-64-bit-applications.md)