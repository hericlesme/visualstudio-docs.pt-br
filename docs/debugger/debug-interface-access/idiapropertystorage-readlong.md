---
title: IDiaPropertyStorage::ReadLONG | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba26ae4e2495d8c0a4feb1ff692d90a228e8292
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Lê `LONG` valores em um conjunto de propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 [in] Identificador da propriedade a ser lido (`PROPID` é definido em WTypes.h como um `ULONG`).  
  
 `pValue`  
 [out] Retorna o valor da propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `E_INVALIDARG` se a propriedade não é do tipo `LONG`.  
  
## <a name="remarks"></a>Comentários  
 Um `LONG` é definido pelo Windows como um inteiro assinado de 32 bits.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)