---
title: Função CvReleaseProvider | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e62e897b56407ab985125361700da60d4e0fdcd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464261"
---
# <a name="cvreleaseprovider-function"></a>Função CvReleaseProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [função CvReleaseProvider](https://docs.microsoft.com/visualstudio/profiling/cvreleaseprovider-function).  
  
Libera o provedor de marcador. A liberação do provedor de marcador não afetará a série de marcador criada anteriormente desse provedor. A série de marcador deve ser liberada separadamente pela chamada CvReleaseMarkerSeries. A falha ao liberar o provedor causa uma perda de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProvider`  
 Contexto de provedor. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK quando o provedor é liberado com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)



