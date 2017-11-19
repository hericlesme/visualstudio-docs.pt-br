---
title: IDiaLoadCallback2::RestrictDBGAccess | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: feebffca2c332466e6f5105c4f69b74744922cf0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
Determina se procurando por informações de depuração é permitida de arquivos. dbg.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT RestrictDBGAccess();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Qualquer valor de retorno diferente de `S_OK` para evitar a busca de informações de depuração de arquivos. dbg.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)