---
title: ': Get_program | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a26982c1827b9d9b4a7ed09e8aa3af61c9141c9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Recupera a cadeia de caracteres do programa que é usada para calcular o registro definido antes da chamada para a função atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna a cadeia de caracteres do programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A cadeia de caracteres do programa é uma sequência de macros que é interpretada para estabelecer o prólogo. Por exemplo, um quadro de pilha típico pode usar a cadeia de caracteres do programa `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. O formato é a notação inversa polonês, onde os operadores siga os operandos. `T0`representa uma variável temporária na pilha. Este exemplo executa as seguintes etapas:  
  
1.  Mover o conteúdo do registro `ebp` para `T0`.  
  
2.  Adicionar `4` o valor em `T0` para produzir um endereço, obter o valor desse endereço e armazenar o valor no registro `eip`.  
  
3.  Obter o valor do endereço armazenado em `T0` e armazene esse valor no registro `ebp`.  
  
4.  Adicionar `8` o valor em `T0` e armazene esse valor no registro `esp`.  
  
 Observe que a cadeia de caracteres do programa é específica para a CPU e a convenção de chamada definido para a função representada pelo quadro de pilhas atual.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)