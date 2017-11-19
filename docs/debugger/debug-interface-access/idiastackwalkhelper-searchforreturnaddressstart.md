---
title: Idiastackwalkhelper | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d949a10e437a3f5b43a85ab9e1a5bf048438c59
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Pesquisa o quadro de pilha especificada para um endereço de retorno ou próximo o endereço de pilha especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT searchForReturnAddressStart(   
   IDiaFrameData*  frame,  
   ULONGLONG       startAddress,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `frame`  
 [in] Um [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto que representa o quadro de pilhas atual.  
  
 `startAddress`  
 [in] Um endereço de memória virtual da qual iniciar a pesquisa.  
  
 `ReturnAddress`  
 [out] Retorna a função mais próxima retornar o endereço para `startAddress`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)