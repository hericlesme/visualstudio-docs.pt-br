---
title: Idialinenumber | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLineNumber::get_relativeVirtualAddress method
ms.assetid: ba8142e3-5c77-43cc-bd33-c077dcc18cab
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93c8d7b80e62b54f045e7f4711a9e590d3d582ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idialinenumbergetrelativevirtualaddress"></a>IDiaLineNumber::get_relativeVirtualAddress
Recupera o endereço virtual relativo (RVA) do bloco.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o endereço virtual relativo da imagem do bloco.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)