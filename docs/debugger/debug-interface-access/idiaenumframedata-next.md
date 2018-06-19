---
title: Idiaenumframedata | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6835cda6c8c2a5cb20135abf92a523a270b32c78
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461236"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Recupera um número especificado de elementos de dados de quadro na sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de elementos de dados do quadro do enumerador a ser recuperado.  
  
 rgelt  
 [out] Uma matriz de [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objetos a ser preenchida com os elementos de dados solicitado do quadro.  
  
 pceltFetched  
 [out] Retorna o número de elementos de dados do quadro do enumerador buscadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhuma mais registros. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)