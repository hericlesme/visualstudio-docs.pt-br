---
title: ': Get_ishotpatchable | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isHotpatchable method
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb3da57daefbcb51b5bcbeb32ec4d06b1e0d3f89
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465597"
---
# <a name="idiasymbolgetishotpatchable"></a>IDiaSymbol::get_isHotpatchable
Recupera um sinalizador que indica se o módulo foi compilado com o [/hotpatch (Criar imagem de Hotpatchable)](/cpp/build/reference/hotpatch-create-hotpatchable-image) opção de compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_isHotpatchable(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFlag`  
 [out] Retorna `TRUE` se o módulo for hot patches; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 Essa propriedade está disponível na `SymTagCompilandDetails` tipo de símbolo (consulte [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V DIA SDK 8.0|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)