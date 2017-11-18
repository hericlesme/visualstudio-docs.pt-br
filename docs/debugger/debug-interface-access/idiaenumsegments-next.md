---
title: Idiaenumsegments | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 210976ad2cbe44d4f94758c9c1fe9d2216e7f44c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Recupera um número de segmentos na sequência de enumeração especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de segmentos no enumerador a ser recuperado.  
  
 rgelt  
 [out] Uma matriz que é preenchido com os detalhes desejados [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objetos que representam os segmentos.  
  
 pceltFetched  
 [out] Retorna o número de segmentos no enumerador busca.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhuma mais segmentos. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)