---
title: ': Get_functionstart | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a54fd51b63bb53521b9f1e9c75f75e49d771b0ba
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458135"
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
Recupera um sinalizador que indica se o bloco contém o ponto de entrada de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se o bloco contiver o ponto de entrada; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 É possível que um quadro de pilha não for o início de uma função, como o quadro representa um método embutido ou uma função inserida em uma função.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)