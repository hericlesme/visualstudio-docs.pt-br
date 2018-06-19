---
title: Idiaenumframedata | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d725c38073b82bc94081b3c27791e88f64343cd3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458103"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Recupera um elemento de quadro de dados por meio de um índice.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 índice  
 [in] Índice da [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto a ser recuperado. O índice está no intervalo de 0 a `count`-1, onde `count` é retornado pelo [Idiaenumframedata](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) método.  
  
 section  
 [out] Retorna um [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto que representa o elemento de dados de quadro desejado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)