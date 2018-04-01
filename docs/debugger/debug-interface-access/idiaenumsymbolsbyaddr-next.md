---
title: Idiaenumsymbolsbyaddr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3256f36e8ab663200a35b3c0fe58933e8559c38e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Recupera os próximos símbolos em ordem por endereço.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de símbolos no enumerador a ser recuperado.  
  
 rgelt  
 [out] Uma matriz que deve ser preenchido com o [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa os símbolos desejados.  
  
 pceltFetched  
 [out] Retorna o número de símbolos no enumerador busca.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum símbolo mais. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método atualizará a posição de enumerador pelo número de elementos buscados.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)