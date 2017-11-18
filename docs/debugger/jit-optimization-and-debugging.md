---
title: "JIT otimização e depuração | Microsoft Docs"
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
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acf75c0fbf6f5c3cfcf645d288c4e5e2eb2450d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="jit-optimization-and-debugging"></a>Otimização e depuração JIT
Quando você depurar um aplicativo gerenciado, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] suprime a otimização de código just-in-time (JIT) por padrão. A supressão da otimização JIT significa que você está depurando código não otimizado. O código é executado um pouco mais lentamente porque não é otimizado, mas sua experiência de depuração é muito mais completa. A depuração de código otimizado é mais difícil e recomendada somente se você encontrar um bug no código otimizado que não pode ser reproduzido na versão não otimizada.  
  
 Otimização JIT é controlada no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pelo **otimização Suppress JIT no carregamento do módulo** opção. Você pode encontrar essa opção no **geral** página sob o **depuração** nó o **opções** caixa de diálogo.  
  
 Se você desmarcar a **otimização Suppress JIT no carregamento do módulo** opção, você pode depurar código otimizado JIT, mas sua capacidade de depuração pode ser limitada porque o código otimizado não coincide com o código-fonte. Como resultado, janelas do depurador, como o **locais** e **Autos** janela não podem exibir as informações que eles seriam se você for depurando código não otimizado.  
  
 Outra diferença importante está relacionada à depuração com Apenas Meu Código. Se você estiver depurando com Apenas Meu Código, o depurador considerará o código otimizado como código de não usuário, que não deve ser exibido durante a depuração. Consequentemente, se estiver depurando código otimizado JIT, provavelmente será conveniente desativar Apenas Meu Código. Para obter mais informações, consulte [restringir passo a passo para apenas meu código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Lembre-se de que o **otimização Suppress JIT no carregamento do módulo** opção suprime a otimização de código quando módulos são carregados. Se você anexar a um processo que já estiver em execução, ele poderá conter código já carregado, compilado por JIT e otimizado. O **otimização Suppress JIT no carregamento do módulo** opção não tem nenhum efeito sobre esse código, embora ela afetará módulos que estão carregados depois que você anexar. Além disso, o **otimização Suppress JIT no carregamento do módulo** opção não afeta módulos, como WinForms, que são criados com NGEN.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Navegar pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo de execução gerenciada](/dotnet/standard/managed-execution-process)