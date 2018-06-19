---
title: Idiaenumsymbols | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65e96f2f03229b12c378a096ecfd7555af1f5cce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459016"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Ignora um número especificado de símbolos em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de símbolos na sequência de enumeração para ignorar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` se não houver nenhum símbolo mais a ignorar.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)