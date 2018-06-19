---
title: ': Get_hasseh | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dcc6cb799b5d218cec09095115a9046605780c65
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31463046"
---
# <a name="idiasymbolgethasseh"></a>IDiaSymbol::get_hasSEH
Recupera um sinalizador que especifica se a função contém qualquer [manipulação de exceções estruturado (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) (por exemplo, Try /\__except blocos).  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_hasSEH(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFlag`  
 [out] Retorna `TRUE` se a função tiver qualquer exceção estruturada tratamento blocos; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V DIA SDK 8.0|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Tratamento de exceções estruturado (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)