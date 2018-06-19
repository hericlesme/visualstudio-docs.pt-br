---
title: ': Get_statement | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c259c7157ad98dee3830e96ca8922b88a2fe56c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459669"
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
Recupera um sinalizador que indica que essas informações de linha descrevem o início de uma instrução, em vez de uma expressão, na origem do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se essas informações de linha descrevem o início de uma instrução na origem do programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Instruções podem abranger várias linhas. Este método indica se o número de linha associada marca o início de tal uma instrução de várias linha.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)