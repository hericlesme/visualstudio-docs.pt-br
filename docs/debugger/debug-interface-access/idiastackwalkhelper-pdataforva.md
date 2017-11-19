---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4925a4a37395dd53fabb1d8d7ba7f80bc5cc6c93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Retorna o bloco de dados PDATA associado ao endereço virtual.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `va`  
 [in] Especifica o endereço virtual para obter os dados.  
  
 `cbData`  
 [in] O tamanho dos dados em bytes para obter.  
  
 `pcbData`  
 [out] Retorna o tamanho real dos dados em bytes, que foi obtido.  
  
 `pbData`  
 [out no] Um buffer é preenchido com os dados solicitados. Não pode ser `NULL`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum PDATA para o endereço especificado. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 PDATA (a seção denominada ". pData") de um compiland contém informações sobre funções de manipulação de exceção.  
  
 O chamador sabe a quantidade de dados a ser retornado para que o chamador tenha sem necessidade de solicitar a quantidade de dados está disponível. Portanto, é aceitável para uma implementação deste método para retornar um erro se o `pbData` parâmetro é `NULL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)