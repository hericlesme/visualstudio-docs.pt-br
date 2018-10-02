---
title: 'Idiastackwalkhelper:: Symbolforva | Microsoft Docs'
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
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d04a504d2f9287e7a807d8b55fb3d644486c9ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475538"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiastackwalkhelper:: Symbolforva](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper-symbolforva).  
  
Recupera o símbolo que contém o endereço virtual especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `va`  
 [in] O endereço virtual que está contido no símbolo de solicitada. O símbolo deve ser um `SymTagFunctionType` (um valor a partir de [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração).  
  
 `ppSymbol`  
 [out] Uma [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o símbolo no endereço especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



