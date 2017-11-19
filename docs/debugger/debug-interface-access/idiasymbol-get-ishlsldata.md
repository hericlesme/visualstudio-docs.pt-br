---
title: IDiaSymbol::get_isHLSLData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38c23148b717ba96ec934d4dc81cade0a9a81794
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetishlsldata"></a>IDiaSymbol::get_isHLSLData
Especifica se este símbolo representa dados de alto nível do sombreador idioma HLSL ().  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_isHLSLData(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Um ponteiro para um `BOOL` que especifica se este símbolo representa dados HLSL.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)