---
title: THUNK_ORDINAL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a2711ab101299b47e954e56fcbbae98d9f5fdb6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Designa os tipos de conversão.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elementos  
 THUNK_ORDINAL_NOTYPE  
 Conversão padrão.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Um `this` conversão adjustor.  
  
 THUNK_ORDINAL_VCALL  
 Conversão de chamada virtual.  
  
 THUNK_ORDINAL_PCODE  
 Conversão de código P.  
  
 THUNK_ORDINAL_LOAD  
 Conversão de carregamento de atraso.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Conversão de trampoline incremental (uma conversão de trampoline é usada para devolver chamadas do espaço de memória para outro).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Conversão de trampoline de ponto de ramificação.  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são retornados de uma chamada para o [: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)