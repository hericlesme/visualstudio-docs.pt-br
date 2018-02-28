---
title: "Caixa de diálogo (exceção lançada) de depurador do Microsoft Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1020711c21fb7171a8f7f8b87296d300f53b78b1
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2018
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Caixa de diálogo Depurador do Microsoft Visual Studio (exceção gerada)
Ocorreu uma exceção no seu programa. Esta caixa de diálogo relata o tipo de exceção lançada. Seu código precisa tratar essa exceção. Você pode escolher entre as seguintes opções para tratar a exceção:  
  
 **Quebra**  
 Permite que a execução seja interrompida no depurador. O manipulador de exceção não será invocado antes da interrupção. Se você continuar a partir da interrupção, o manipulador de exceção será invocado.  
  
 **Continue**  
 Permite que a execução continue, dando ao manipulador de exceção a possibilidade de tratar a exceção. Essa opção não está disponível para determinados tipos de exceções. **Continuar** permitirá que o aplicativo continuar. Em um aplicativo nativo, ela fará com que a exceção seja relançada. Em um aplicativo gerenciado, ela fará com que o programa seja encerrado ou a exceção seja tratada por um aplicativo de hospedagem.  
  
> [!NOTE]
>  Você não pode continuar depois de uma exceção sem tratamento em código gerenciado. Escolhendo **continuar** depois de depuração a parar faz com que uma exceção sem tratamento no código gerenciado.  
  
 **Ignorar**  
 Permite que a execução continue sem invocar o manipulador de exceção. Como o manipulador de exceção não é invocado, isso poderá resultar em outras consequências, incluindo erros e exceções adicionais. Essa opção não está disponível para determinados tipos de exceções.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)   
 [Práticas recomendadas para exceções](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [Tratamento de Exceção](/cpp/windows/exception-handling-cpp-component-extensions)