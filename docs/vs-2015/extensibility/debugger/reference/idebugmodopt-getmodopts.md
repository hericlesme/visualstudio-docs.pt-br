---
title: IDebugModOpt::GetModOpts | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 344a2640cf550d9e2025c6ccb9aec28a0eb98895
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462207"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugModOpt::GetModOpts](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodopt-getmodopts).  
  
Recupera uma lista de modificadores opcionais.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] Número de elementos a serem retornados.  
  
 `rgelt`  
 [out] Retorna uma matriz que contém as opções.  
  
 `pceltFetched`  
 [no, out] Número de elementos retornados no `rgelt` matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)

