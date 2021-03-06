---
title: Funções de gancho de relatório | Microsoft Docs
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
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b9a87a9efe91c8a3739b88a39fac5c391218833
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467220"
---
# <a name="report-hook-functions"></a>Funções de gancho do relatório
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [funções de gancho de relatório](https://docs.microsoft.com/visualstudio/debugger/report-hook-functions).  
  
Uma função de gancho de relatório, instalada usando [crtsetreporthook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), é chamado toda vez [crtdbgreport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) gera um relatório de depuração. Você pode usá-la, entre outras coisas, para filtrar relatórios com foco em tipos de alocações específicos. Uma função de gancho de relatório deve ter um protótipo como o seguinte:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 O ponteiro que você passa para **crtsetreporthook** é do tipo **crt_report_hook**, conforme definido em CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quando a biblioteca de tempo de execução chama sua função de gancho, o *nRptType* argumento contém a categoria do relatório (**_CRT_WARN**, **crt_error**, ou **_CRT Macros Assert**), *szMsg* contém um ponteiro para uma cadeia de caracteres de mensagem de relatório completamente montado, e *retVal* Especifica se `_CrtDbgReport` devem continuar em execução normal Depois de gerar o relatório ou inicie o depurador. (Um *retVal* valor igual a zero continua a execução, um valor de 1 inicia o depurador.)  
  
 Se o gancho tratar a mensagem em questão completamente, para que nenhum relatório adicional seja necessária, ele deverá retornar **verdadeira**. Se ele retornar **falsos**, `_CrtDbgReport` relatará a mensagem normalmente.  
  
## <a name="see-also"></a>Consulte também  
 [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)   
 [Exemplo de crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



