---
title: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Microsoft Docs
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
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ea4bf723ecccbd04c7a6ee2a9b3f2b57e72c7dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474789"
---
# <a name="idiasymbolgetliverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress).  
  
Retorna o início do intervalo de endereço no qual o símbolo local é válido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_liveRangeStartRelativeVirtualAddress (   
   DWORD* address  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [out] Retorna o início do intervalo de endereços.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. O endereço virtual relativo retornado é o início do intervalo no qual o símbolo é válido.  
  
> [!NOTE]
>  Um código de erro retornado significa que o símbolo não tem informações de intervalo em tempo real.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



