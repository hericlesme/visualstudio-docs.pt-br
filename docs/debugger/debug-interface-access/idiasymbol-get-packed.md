---
title: ': Get_packed | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f124a27bb05e77d52bebde9f97dc81ea1fc971bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479507"
---
# <a name="idiasymbolgetpacked"></a>IDiaSymbol::get_packed
Recupera um sinalizador que especifica se o tipo de dados definido pelo usuário (UDT) é compactado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_packed (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se o UDT é fornecido; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 Pacote significa que todos os membros da UDT são posicionados mais próximos possível, sem nenhum preenchimento intermediário para alinhar aos limites de memória.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)