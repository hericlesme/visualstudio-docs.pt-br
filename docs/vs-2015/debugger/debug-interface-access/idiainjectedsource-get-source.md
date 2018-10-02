---
title: 'Idiainjectedsource:: Get_source | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a608da39e0d1c77cb149bd3cfda49506ecab893
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462716"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiainjectedsource:: Get_source](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiainjectedsource-get-source).  
  
Recupera os bytes de código de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cbData`  
 [in] O número de bytes que representa o tamanho do buffer de dados.  
  
 `pcbData`  
 [out] Retorna o número de bytes que representa os bytes retornados. Se `data` está `NULL`, em seguida, `pcbData` é o número total de bytes de dados disponíveis.  
  
 `data[]`  
 [out] Um buffer que deve ser preenchida com os bytes de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)



