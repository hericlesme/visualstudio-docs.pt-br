---
title: IDiaSymbol::get_isSingleInheritance | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4481fd4517db89867ca21b137af454980f60de26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetissingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
Especifica se o `this` ponteiro aponta para um membro de dados com herança única.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_isSingleInheritance(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Um ponteiro para um `BOOL` que especifica se o `this` ponteiro aponta para um membro de dados com herança única.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)