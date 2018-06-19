---
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7df83017e60a9d3600c7e49bcf888c771a748cee
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461487"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Retorna uma enumeração de símbolos para que o valor da marca especificado corresponde à variável na função de stub do acelerador pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `parent`  
 [in] Um IDiaSymbol que corresponde à função de stub Acelerador a ser pesquisada.  
  
 `tagValue`  
 [in] O valor de marca do ponteiro.  
  
 `ppResult`  
 [out] Um ponteiro para um `IDiaEnumSymbols` ponteiro de interface que é inicializado com o resultado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)