---
title: Idiaenumsourcefiles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1fda746edf51771e7927efd03094f42903141e6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458337"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Recupera um arquivo de origem por meio de um índice.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 índice  
 [in] Índice da [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto a ser recuperado. O índice está no intervalo de 0 a `count`-1, onde `count` é retornado pelo [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) método.  
  
 arquivo de origem  
 [out] Retorna um [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto que representa o arquivo de fonte desejado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)