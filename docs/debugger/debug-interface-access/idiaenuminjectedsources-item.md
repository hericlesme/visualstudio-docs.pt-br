---
title: Idiaenuminjectedsources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7fb753605a85dedefac5fc2cd33f4baf158b128b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31456862"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Recupera uma fonte injetada por meio de um índice.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 índice  
 [in] Índice da [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) objeto a ser recuperado. O índice é o intervalo de 0 a `count`-1, onde `count` é retornado pelo [Idiaenuminjectedsources](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) método.  
  
 injectedSource  
 [out] Retorna um [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) objeto que representa a fonte injetada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)