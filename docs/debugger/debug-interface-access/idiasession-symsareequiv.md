---
title: ': Symsareequiv | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc92a38305e7cc8c74b4ada0d560b314ed92da8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460037"
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