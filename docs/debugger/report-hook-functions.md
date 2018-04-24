---
title: Funções de gancho de relatório | Microsoft Docs
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
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 562944404d3e02a2e5768fcd74c67302475e6190
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="report-hook-functions"></a>Funções de gancho do relatório
Uma função de gancho de relatório, instalada usando [crtsetreporthook](/cpp/c-runtime-library/reference/crtsetreporthook), é chamado sempre [crtdbgreport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) gera um relatório de depuração. Você pode usá-la, entre outras coisas, para filtrar relatórios com foco em tipos de alocações específicos. Uma função de gancho de relatório deve ter um protótipo como o seguinte:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 O ponteiro transmitido **crtsetreporthook** é do tipo **crt_report_hook**, conforme definido em CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quando a biblioteca de tempo de execução chama a função de gancho de *nRptType* argumento contém a categoria do relatório (**_CRT_WARN**, **_CRT_ERROR**, ou **_CRT Assert**), *szMsg* contém um ponteiro para uma cadeia de caracteres de mensagem de relatório totalmente montado e *retVal* Especifica se `_CrtDbgReport` devem continuar em execução normal Depois de gerar o relatório ou iniciar o depurador. (Um *retVal* valor zero continua a execução, um valor de 1 inicia o depurador.)  
  
 Se o gancho trata a mensagem em questão completamente, de forma que nenhum relatório adicional é necessária, ele deverá retornar **TRUE**. Se ele retorna **FALSE**, `_CrtDbgReport` relatará a mensagem normalmente.  
  
## <a name="see-also"></a>Consulte também  
 [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)   
 [Exemplo de crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)