---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Microsoft Docs
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
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 965991aa2f4b65a369bf051dc008b6dd21b0cfb5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464898"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDiaSymbol::get_numberOfAcceleratorPointerTags](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags).  
  
Retorna o número de marcas de ponteiro de acelerador em uma função de stub do C++ AMP.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `count`  
 [out] Um ponteiro para um `DWORD` que contém o número de acelerador de marcas de ponteiro em uma função de stub do C++ AMP.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado em um `IDiaSymbol` interface que corresponde a uma função de stub do acelerador de C++ AMP.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



