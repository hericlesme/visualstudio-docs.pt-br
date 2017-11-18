---
title: ': Symsareequiv | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 776e3868e8529657fb77cc9fac1d42eb04cdd722
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Verifica se os dois símbolos são equivalentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `symbolA`  
 [in] A primeira [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto usado na comparação.  
  
 `symbolB`  
 [in] O segundo `IDiaSymbol` objeto usado na comparação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se os símbolos forem equivalentes, retorna `S_OK`; caso contrário, retorna `S_FALSE`, os símbolos não são equivalentes. Caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)