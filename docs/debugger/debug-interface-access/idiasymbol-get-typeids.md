---
title: ': Get_typeids | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed742971a75d15eccfd6765dbaf242f0afc7890
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Recupera uma matriz de valores de identificador de tipo específico de compilador para esse símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cTypeIds`  
 [in] Tamanho do buffer para armazenar os dados.  
  
 `pcTypeIds`  
 [out] Retorna o número de `typeIds` gravado, ou, se `typeIds` é `NULL`, em seguida, o número total de identificadores de tipo disponíveis.  
  
 `typeIds[]`  
 [out] Uma matriz que é preenchido com os identificadores de tipo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)