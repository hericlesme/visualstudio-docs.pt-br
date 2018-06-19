---
title: ': Symbolforva | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e70dac639f18f934bb997cc4979bdbe6a7d8c4c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467531"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Recupera o símbolo que contém o endereço virtual especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `va`  
 [in] O endereço virtual que está contido no símbolo de solicitada. O símbolo deve ser um `SymTagFunctionType` (um valor da [SymTagEnum enumeração](../../debugger/debug-interface-access/symtagenum.md) enumeração).  
  
 `ppSymbol`  
 [out] Um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o símbolo no endereço especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)