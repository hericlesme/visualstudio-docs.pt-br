---
title: Idiaenumlinenumbers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a00929311c1e8ccaa50d03543f072696bd2bf7f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468418"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Recupera um número de linha por meio de um índice.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 índice  
 [in] Índice da [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) objeto a ser recuperado. O índice está no intervalo de 0 a `count`-1, onde `count` é retornado pelo [Idiaenumlinenumbers](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) método.  
  
 lineNumber  
 [out] Retorna um [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) objeto que representa o número de linha desejado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)