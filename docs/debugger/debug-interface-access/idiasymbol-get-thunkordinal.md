---
title: ': Get_thunkordinal | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed649ffe02cc27f959bf96b826fc02498beb4acd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Recupera o tipo de conversão de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna um valor da [enumeração THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) enumeração que especifica o tipo de conversão de uma função.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 Essa propriedade é válida somente se o símbolo como um [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valor `SymTagThunk`.  
  
 Uma "conversão" é um trecho de código que converte entre um espaço de endereço de memória de 32 bits (também conhecido como o espaço de endereço simples) e um espaço de endereço de 16 bits (conhecido como um espaço de endereço segmentado).  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)