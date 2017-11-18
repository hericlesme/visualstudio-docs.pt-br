---
title: BasicType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f93fa1380dbb2d7623cddec3780593cd50513f2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="basictype"></a>BasicType
Especifica o tipo básico do símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elementos  
 btNoType  
 Nenhum tipo básico é especificado.  
  
 btVoid  
 O tipo básico é um `void`.  
  
 btChar  
 O tipo básico é um `char` (tipo de C/C++).  
  
 btWChar  
 Tipo básico é um caractere (Unicode) largo (`WCHAR`).  
  
 btInt  
 O tipo básico é `signed int` (tipo de C/C++).  
  
 btUInt  
 O tipo básico é `unsigned int` (tipo de C/C++).  
  
 btFloat  
 Tipo básico é um número de ponto flutuante (`FLOAT`).  
  
 btBCD  
 Tipo básico é um decimal codificado binário (`BCD`).  
  
 btBool  
 Tipo básico é um valor booliano (`BOOL`).  
  
 btLong  
 O tipo básico é um `long int` (tipo de C/C++).  
  
 btULong  
 O tipo básico é um `unsigned long int` (tipo de C/C++).  
  
 btCurrency  
 O tipo básico é moeda.  
  
 btDate  
 Tipo básico é data/hora (`DATE`).  
  
 btVariant  
 Tipo básico é uma estrutura de tipo de variável (`VARIANT`).  
  
 btComplex  
 Tipo básico é um número complexo.  
  
 btBit  
 O tipo básico é um bit.  
  
 btBSTR  
 Tipo básico é uma cadeia de caracteres binária ou básica (`BSTR`).  
  
 btHresult  
 O tipo básico é um `HRESULT`.  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são retornados pelo [: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)