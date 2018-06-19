---
title: ': Get_hassetjump | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSetJump method
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e426cad156c79ac532154a201785fed8ed47884
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464281"
---
# <a name="idiasymbolgethassetjump"></a>IDiaSymbol::get_hasSetJump
Recupera um sinalizador que especifica se a função contém um uso o [setjmp](/cpp/c-runtime-library/reference/setjmp) comando (emparelhado com o [longjmp](/cpp/c-runtime-library/reference/longjmp) de comando, eles formam o método de estilo C de tratamento de exceções).  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_hasSetJump(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFlag`  
 [out] Retorna `TRUE` se a função contém um `setjmp` comando; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V DIA SDK 8.0|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [: Get_haslongjump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)   
 [longjmp](/cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/cpp/c-runtime-library/reference/setjmp)