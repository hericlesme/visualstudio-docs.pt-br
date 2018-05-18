---
title: Função CvReleaseProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e4620a4322fedb7fb6337c3f4fd7cb7e22b39df
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2018
---
# <a name="cvreleaseprovider-function"></a>Função CvReleaseProvider
Libera o provedor de marcador. A liberação do provedor de marcador não afetará a série de marcador criada anteriormente desse provedor. A série de marcador deve ser liberada separadamente pela chamada CvReleaseMarkerSeries. A falha ao liberar o provedor causa uma perda de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```C  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProvider`  
 Contexto de provedor. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK quando o provedor é liberado com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)