---
title: 'Idiasymbol:: Get_noinline | Microsoft Docs'
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
- IDiaSymbol::get_noInline method
ms.assetid: 5c610b78-f1a3-494a-acf8-c42b97935be1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12a64732b22a97a04c86d75d10c914aedc8ba687
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473290"
---
# <a name="idiasymbolgetnoinline"></a>IDiaSymbol::get_noInline
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiasymbol:: Get_noinline](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-noinline).  
  
Recupera um sinalizador que especifica se a função foi marcada como não sendo embutido (usando o [noinline](http://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) atributo).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT get_noInline(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFlag`  
 [out] Retorna `TRUE` se a função tem o `noinline` atributo; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V DIA SDK 8.0|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [noinline](http://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42)



