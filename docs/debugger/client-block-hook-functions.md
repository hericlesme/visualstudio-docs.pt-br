---
title: Funções de gancho do bloco de cliente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eccc1781174394da333d2fc703fec0b4d31e522a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457225"
---
# <a name="client-block-hook-functions"></a>Funções de gancho do bloco de clientes
Se você quiser validar ou reportar o conteúdo dos dados armazenados em blocos `_CLIENT_BLOCK`, poderá escrever uma função especificamente para essa finalidade. A função que você escreve deverá ter um protótipo semelhante ao seguinte, conforme definido em CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Em outras palavras, a função de gancho deve aceitar um **void** ponteiro no início do bloco de alocação, junto com um **size_t** digite um valor que indica o tamanho da alocação e retornar `void`. Além disso, o conteúdo depende de você.  
  
 Depois de instalar a função de gancho usando [crtsetdumpclient](/cpp/c-runtime-library/reference/crtsetdumpclient), ele será chamado sempre que uma `_CLIENT_BLOCK` bloco é despejado. Você pode usar [crtreportblocktype](/cpp/c-runtime-library/reference/crtreportblocktype) para obter informações sobre o tipo ou subtipo de blocos despejados.  
  
 O ponteiro para a função que você passa para `_CrtSetDumpClient` é do tipo **crt_dump_client**, conforme definido em CRTDBG. H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)   
 [Exemplo de crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)