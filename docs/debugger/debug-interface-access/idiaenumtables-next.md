---
title: Idiaenumtables | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a2a3d208bc430f95d003dfd40c5831cabf7d2c5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459052"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Recupera um número especificado de tabelas na sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de tabelas no enumerador a ser recuperado.  
  
 `rgelt`  
 [out] Uma matriz que deve ser preenchido com o [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objetos que representam as tabelas desejadas.  
  
 `pceltFetched`  
 [out] Retorna o número de tabelas no enumerador busca.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não existem mais tabelas. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)