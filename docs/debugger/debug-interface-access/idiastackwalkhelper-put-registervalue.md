---
title: IDiaStackWalkHelper::put_registerValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abfd209e5c2f59a0c55128eb235fda868f4bfd5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
Define o valor de um registro.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `index`  
 [in] Um valor da [enumeração CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) enumeração que especifica o registro para gravar.  
  
 `NewVal`  
 [in] O novo valor do registro.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Apesar do tamanho do valor, uma implementação deve armazenar apenas o que o registro normalmente contém. Por exemplo, um registro de 8 bits deveria conter apenas o mais baixo 8 bits do valor especificado.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeração CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)