---
title: "Funções de gancho de alocação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9147439d6aab7a6393f37f0cf8b14b0b0401ed1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="allocation-hook-functions"></a>Funções de gancho da alocação
Uma função de gancho de alocação, instalada usando [crtsetallochook](/cpp/c-runtime-library/reference/crtsetallochook), é chamado sempre que a memória é alocada, realocada ou liberada. Esse tipo de gancho pode ser usada para muitas finalidades diferentes. Use-o para testar como um aplicativo trata situações de memória insuficiente, por exemplo, ou para examinar padrões de alocação ou registrar informações de alocação para análise posterior.  
  
> [!NOTE]
>  Lembre-se da restrição sobre como usar funções de biblioteca de tempo de execução do C em uma função de gancho de alocação, descrita em [ganchos de alocação e alocações de memória de tempo de execução do C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Uma função de gancho de alocação deve ter um protótipo como o seguinte:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 O ponteiro transmitido [crtsetallochook](/cpp/c-runtime-library/reference/crtsetallochook) é do tipo **crt_alloc_hook**, conforme definido em CRTDBG. H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Quando a biblioteca de tempo de execução chama o gancho do *nAllocType* argumento indica qual alocação operação está prestes a ser executada (**_HOOK_ALLOC**, **_HOOK_REALLOC**, ou **_HOOK_FREE**). No caso de uma alocação livre ou realocação, o `pvData` contém um ponteiro para o tópico de usuário do bloco que está para ser liberado. No entanto, no caso de uma alocação, esse ponteiro é nulo, porque a alocação ainda não ocorreu. Os argumentos restantes contêm o tamanho da alocação em questão, seu tipo de bloco, o número sequencial da solicitação associado a ele e um ponteiro para o nome de arquivo e o número de linha nos quais a alocação foi feita, se houver. Depois que a função de gancho executa qualquer análise e outras tarefas que queira seu autor, ele deve retornar **TRUE**, indicando que a operação de alocação pode continuar, ou **FALSE**, indicando que o a operação deve falhar. Um gancho simple desse tipo pode verificar a quantidade de memória alocada até o momento e retornar **FALSE** se essa quantidade excedeu um limite pequeno. O aplicativo apresentaria o tipo de erros de alocação que ocorreriam normalmente apenas quando a memória disponível estivesse muito baixa. Ganchos mais complexos podem controlar os padrões de alocação, analisar o uso de memória ou reportar quando as situações específicas surgem.  
  
## <a name="see-also"></a>Consulte também  
 [Ganchos de alocação e alocações de memória de tempo de execução do C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)   
 [Exemplo de crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)