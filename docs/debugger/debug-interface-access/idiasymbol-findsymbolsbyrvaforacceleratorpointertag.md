---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d96e58f19ae4170430488bc33e454d70944c36af
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Dado um valor de marca correspondente, esse método retorna uma enumeração de símbolos que estão contidos nesta função stub num endereço virtual relativo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `tagValue`  
 [in] O valor de marca de ponteiro para o qual os registros de símbolo pointee são encontrados.  
  
 `rva`  
 [in] Rva que é usado para filtrar os símbolos que correspondem à variável pointee com o valor da marca especificado.  
  
 `ppResult`  
 [out] Um ponteiro para um `IDiaEnumSymbols` ponteiro de interface que é inicializado com o resultado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame este método somente em um `IDiaSymbol` interface que corresponde a uma função de stub do acelerador.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)