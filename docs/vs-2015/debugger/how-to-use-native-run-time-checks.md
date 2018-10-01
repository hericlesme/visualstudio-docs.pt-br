---
title: 'Como: usar verificações de tempo de execução nativas | Microsoft Docs'
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
- c.runtime.errorchecks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e90af82b5f3d7cd88d3b8488b0ebd9a4359b566f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462691"
---
# <a name="how-to-use-native-run-time-checks"></a>Como usar verificações de tempo de execução nativas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: usar verificações de tempo de execução nativo](https://docs.microsoft.com/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
No Visual C++, você pode usar nativos [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) para capturar erros comuns de tempo de execução, como:  
  
-   Dano do ponteiro de pilha.  
  
-   Excesso de matrizes locais.  
  
-   Dano de pilha.  
  
-   Dependências em variáveis locais não inicializadas.  
  
-   Perda de dados em uma atribuição para uma variável mais curta.  
  
 Se você usar **/RTC** com um otimizado (**/O**) criar um resultados de erro do compilador. Se você usar um pragma `runtime_checks` em uma construção otimizada, o pragma não terá nenhum efeito.  
  
 Quando você depurar um programa que tem as verificações de tempo de execução habilitadas, a ação padrão será para o programa parar e interromper no depurador quando ocorrer um erro em tempo de execução. Você pode alterar este comportamento padrão para qualquer verificação de tempo de execução. Para obter mais informações, consulte [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Os procedimentos a seguir descrevem como habilitar as verificações nativas de tempo de execução em uma compilação de depuração e como modificar o comportamento nativo de verificação de tempo de execução.  
  
 Outros tópicos desta seção fornecem informações sobre:  
  
-   [Personalizar o tempo de execução verifica com a biblioteca de tempo de execução C](../debugger/native-run-time-checks-customization.md)  
  
-   [Usar o tempo de execução verifica sem a biblioteca de tempo de execução C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Para habilitar as verificações de tempo de execução nativas em uma compilação de depuração  
  
-   Use o **/RTC** opção e vincule com a versão de depuração de uma biblioteca de tempo de execução do C (/ MDd, por exemplo).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Para modificar o comportamento nativo de verificação de tempo de execução  
  
-   Use o pragma `runtime_checks`.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Verificação de erros em tempo de execução](http://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)





