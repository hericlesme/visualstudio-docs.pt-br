---
title: ': Get_rank | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f4929f892520924e34ab78dac3a9691c7d43a504
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Recupera a posição (número de dimensões) de uma matriz multidimensional FORTRAN.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o número de dimensões em uma matriz multidimensional FORTRAN.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 Classificação refere-se ao número de dimensões em uma matriz, onde a matriz é declarada como `myarray[1,2,3]`. Este exemplo tem uma classificação de dimensões 3 e 3. Classificação não é aplicável ao C++ que usa o conceito de uma matriz de matrizes para cada dimensão (ou seja, `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)