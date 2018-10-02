---
title: 'Idiaenumtables:: clone | Microsoft Docs'
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
- IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfb80dcf97fd47404f262da46c7aad08b91f6830
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464251"
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiaenumtables:: clone](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumtables-clone).  
  
Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumTables** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppenum`  
 [out] Retorna um [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) objeto que contém uma duplicata do enumerador. As tabelas não são duplicadas, apenas o enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)



