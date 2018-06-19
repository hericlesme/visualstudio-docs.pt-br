---
title: Idiaenumlinenumbers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Skip method
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebaa7366128a02b9ac0af253c418650a747b657e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31456696"
---
# <a name="idiaenumlinenumbersskip"></a>IDiaEnumLineNumbers::Skip
Ignora um número especificado de números de linha em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de números de linha na sequência de enumeração para ignorar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` se não houver nenhum números de linha mais a ignorar.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)