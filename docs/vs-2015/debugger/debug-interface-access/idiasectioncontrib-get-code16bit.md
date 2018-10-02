---
title: IDiaSectionContrib::get_code16bit | Microsoft Docs
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
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02573347eec6ff8571ead397ea057bf991f0faf9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460685"
---
# <a name="idiasectioncontribgetcode16bit"></a>IDiaSectionContrib::get_code16bit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDiaSectionContrib::get_code16bit](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasectioncontrib-get-code16bit).  
  
Recupera um sinalizador que indica se a seção contém código de 16 bits.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_code16bit(  
   BOOL *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se o código na seção de 16 bits; caso contrário, retorna `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método só indica se o código de 16 bits. Se o código é não de 16 bits, ele pode ser qualquer outra coisa, como o código de 32 bits ou 64 bits.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



