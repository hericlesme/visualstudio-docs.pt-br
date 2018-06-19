---
title: ': Get_write | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_write method
ms.assetid: 7e75348e-c12c-44ec-b004-e97767580a3f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa9e8fa933e5a023298ab962025500f14fd05028
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460678"
---
# <a name="idiasectioncontribgetwrite"></a>IDiaSectionContrib::get_write
Recupera um sinalizador que indica se a seção pode ser modificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_write (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se a seção pode ser gravada como; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)