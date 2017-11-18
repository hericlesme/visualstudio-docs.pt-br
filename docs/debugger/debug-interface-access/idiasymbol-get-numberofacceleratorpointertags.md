---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4d7145903269822fbc67d0894cbbea1530044e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Retorna o número de marcas de ponteiro accelerator em uma função de stub do C++ AMP.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `count`  
 [out] Um ponteiro para um `DWORD` que contém o número de acelerador de marcas de ponteiro em uma função de stub do C++ AMP.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado em um `IDiaSymbol` interface que corresponde a uma função de stub do C++ AMP acelerador.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)