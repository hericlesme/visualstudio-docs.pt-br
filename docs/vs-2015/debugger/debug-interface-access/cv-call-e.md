---
title: CV_call_e | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d4d001b1c6c2df10b8263fa9b0c5f5be360c9e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462278"
---
# <a name="cvcalle"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CV_call_e](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/cv-call-e).  
  
Especifica a convenção de chamada para uma função.  
  
> [!NOTE]
>  Somente os valores de enumeração mais comuns são documentados aqui. A enumeração completa está disponível no arquivo de cabeçalho cvconst.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 Especifica uma convenção de chamada de função usando um próximo envio por push da direita para esquerda. A função chamada limpa a pilha.  
  
 CV_CALL_NEAR_FAST  
 Especifica uma convenção de chamada de função usando um próximo envio por push da esquerda para a direita com registros. A função chamada usa a soma dos bytes de parâmetro para limpar a pilha.  
  
 CV_CALL_NEAR_STD  
 Especifica uma convenção de chamada de função usando uma chamada padrão quase (push da direita para esquerda).  
  
 CV_CALL_NEAR_SYS  
 Especifica uma convenção de chamada de função usando uma chamada de sistema quase.  
  
 CV_CALL_THISCALL  
 Especifica uma convenção de chamada de função usando `this` chamar (`this` ponteiro passados no registro).  
  
 CV_CALL_CLRCALL  
 Especifica uma convenção de chamada de função usada pelo tempo de execução do CLR (Common Language) (também conhecido como um código gerenciado convenção de chamada).  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são retornados por uma chamada para o [idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)



