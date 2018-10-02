---
title: 'Idiasymbol:: Get_issafebuffers | Microsoft Docs'
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
- IDiaSymbol::get_isSafeBuffers method
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a2268efc23ba9a0410be9419211fe2f0f8a0035
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467328"
---
# <a name="idiasymbolgetissafebuffers"></a>IDiaSymbol::get_isSafeBuffers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiasymbol:: Get_issafebuffers](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-issafebuffers).  
  
Recupera um sinalizador que especifica se a diretiva de pré-processador para um buffer seguro é usada. Usado quando o [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) é definido como `SymTagFunction`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_isSafeBuffers(   
   BOOL* pRetVal)  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se o ponteiro usa uma diretiva de pré-processador para um buffer seguro; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [strict_gs_check](http://msdn.microsoft.com/library/decfec81-c916-42e0-a07f-8cc26df6a7ce)



