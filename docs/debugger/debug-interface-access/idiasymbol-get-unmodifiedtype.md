---
title: ': Get_unmodifiedtype | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a24b85ac16f9837a4e28674567341f00a993bf9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetunmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
Recupera o tipo original para esse símbolo. Usado quando o [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) é definido como um tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o tipo original desse símbolo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 O tipo atual é uma modificação do tipo original retornado. O tipo original para um símbolo pode ser determinado pelo primeiro obter o tipo de símbolo e, em seguida, interrogar que retornado para o tipo original. Observe que alguns símbolos não podem ter um tipo de modificação do tipo original.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)