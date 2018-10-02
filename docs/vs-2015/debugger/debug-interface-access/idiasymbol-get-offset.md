---
title: 'Idiasymbol:: Get_offset | Microsoft Docs'
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
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1de1a7ed53c1f252958c70001b1609b82e715078
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474189"
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiasymbol:: Get_offset](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-offset).  
  
Recupera o deslocamento do local do símbolo. Usado quando o [enumeração LocationType](../../debugger/debug-interface-access/locationtype.md) é `LocIsRegRel` ou `LocIsBitField`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o deslocamento em bytes, do local do símbolo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 O deslocamento é de algum ponto conhecido anteriormente foi determinado. Por exemplo, o deslocamento para um `LocIsBitField` normalmente é o tipo de local desde o início da classe recipiente.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)



