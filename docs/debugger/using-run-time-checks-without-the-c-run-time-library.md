---
title: "Usar o tempo de execução verifica sem a biblioteca de tempo de execução C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb4cef71a9e9557b5a12a7dfe857d67b22dc69b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Usando verificações de tempo de execução sem a biblioteca em tempo de execução do C
Se você vincular seu programa sem a biblioteca de tempo de execução C, usando **/NODEFAULTLIB**e deseja usar verificações em tempo de execução, você deve vincular com RunTmChk.lib.  
  
 O `_RTC_Initialize` inicializa o programa para verificações de tempo de execução. Se você não se vincular à biblioteca em tempo de execução C, deverá verificar se o programa é compilado com verificações de erro em tempo de execução antes de chamar o `_RTC_Initialize`, do seguinte modo:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Se você não se vincular à biblioteca em tempo de execução C, também deverá definir uma função chamada `_CRT_RTC_INITW`. O `_CRT_RTC_INITW` instala a função definida pelo usuário como a função padrão de relatório de erros, do seguinte modo:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Depois de instalar a função padrão de relatório de erros, você poderá instalar funções adicionais de relatório de erros com `_RTC_SetErrorFuncW`. Para obter mais informações, consulte [RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).  
  
## <a name="see-also"></a>Consulte também  
 [Como usar verificações de tempo de execução nativas](../debugger/how-to-use-native-run-time-checks.md)