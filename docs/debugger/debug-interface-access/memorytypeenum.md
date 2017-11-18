---
title: MemoryTypeEnum | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db6a66f8d496c73d05e05fd2f5398998c0a72484
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Especifica o tipo de memória para acessar.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `MemTypeCode`  
 Acessa somente código de memória.  
  
 `MemTypeData`  
 Memória acessa dados ou de pilha.  
  
 `MemTypeStack`  
 Acessa somente pilha de memória.  
  
 `MemTypeAny`  
 Acessa qualquer tipo de memória.  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são passados para o [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) método para limitar o acesso a diferentes tipos de memória.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)