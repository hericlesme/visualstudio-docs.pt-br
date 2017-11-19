---
title: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fe43b99ce430e1e06683494fdeb1c5716b30cea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetliverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Retorna o início do intervalo de endereço no qual o símbolo local é válido.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_liveRangeStartRelativeVirtualAddress (   
   DWORD* address  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [out] Retorna o início do intervalo de endereços.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. O endereço virtual relativo retornado é o início do intervalo no qual o símbolo é válido.  
  
> [!NOTE]
>  Um código de erro significa que o símbolo não tem informações de intervalo dinâmico.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)