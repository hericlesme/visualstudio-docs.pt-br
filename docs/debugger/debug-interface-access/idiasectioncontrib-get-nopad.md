---
title: ': Get_nopad | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b26005e6e7062fcf5a3a6f0a9aba4ac7a79b92f7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461009"
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
Recupera um sinalizador que indica se a seção não deve ser preenchida para o próximo limite de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se a seção não deve ser preenchida para o próximo limite de memória; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esta é uma propriedade geralmente é vista somente em arquivos mais antigos.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)