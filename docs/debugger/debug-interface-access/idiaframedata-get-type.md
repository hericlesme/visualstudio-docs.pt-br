---
title: Idiaframedata | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 127b1314b2d56d39595843895dee795c2db6abce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Recupera o tipo de quadro específico do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna um valor da [enumeração StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md) enumeração que indica o tipo de quadro específico do compilador.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Enumeração StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)