---
title: 'Idiasession:: Findsymbolbyrvaex | Microsoft Docs'
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
- IDiaSession::findSymbolByRVAEx method
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f9c938439fde85104b5206430c8d7b4f991a067
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462075"
---
# <a name="idiasessionfindsymbolbyrvaex"></a>IDiaSession::findSymbolByRVAEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiasession:: Findsymbolbyrvaex](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findsymbolbyrvaex).  
  
Recupera um tipo de símbolo especificado que contém ou está mais próximo de um endereço especificado virtual relativo (RVA) e o deslocamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT findSymbolByRVAEx (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rva`  
 [in] Especifica o RVA.  
  
 `symtag`  
 [in] Tipo de símbolo a ser localizada. Valores são tirados de [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração.  
  
 `ppSymbol`  
 [out] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperado do objeto que representa o símbolo.  
  
 `displacement`  
 [out] Retorna um valor que especifica um deslocamento do endereço virtual relativo especificado em `rva`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



