---
title: CV_call_e | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 54447dac0f070ae97cf5b4c6b421c8d6a0e2d44a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cvcalle"></a>CV_call_e
Especifica a convenção de chamada para uma função.  
  
> [!NOTE]
>  Somente os valores de enumeração mais comuns são documentados aqui. A enumeração completa está disponível no arquivo de cabeçalho cvconst.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elementos  
 CV_CALL_NEAR_C  
 Especifica uma convenção de chamada de função usando um próximo envio por push da direita para esquerda. A função de chamada limpa a pilha.  
  
 CV_CALL_NEAR_FAST  
 Especifica uma convenção de chamada de função usando um próximo envio por push da esquerda para a direita com registros. A função chamada usa a soma de bytes de parâmetro para limpar a pilha.  
  
 CV_CALL_NEAR_STD  
 Especifica uma convenção de chamada de função usando uma chamada near padrão (push da direita para esquerda).  
  
 CV_CALL_NEAR_SYS  
 Especifica uma convenção de chamada de função usando uma próxima chamada do sistema.  
  
 CV_CALL_THISCALL  
 Especifica uma convenção de chamada de função usando `this` chamar (`this` ponteiro transmitido no registro).  
  
 CV_CALL_CLRCALL  
 Especifica uma convenção de chamada de função usada, o tempo de execução do CLR (Common Language) (também conhecido como um código gerenciado convenção de chamada).  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são retornados por uma chamada para o [: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)