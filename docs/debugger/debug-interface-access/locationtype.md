---
title: LocationType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb46eb1c7477f93ed63dfc4424d881886c8d0c8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="locationtype"></a>LocationType
Indica o tipo de informações de localização contidos em um símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Elementos  
 `LocIsNull`  
 Informações de local não estão disponíveis.  
  
 `LocIsStatic`  
 Local é estático.  
  
 `LocIsTLS`  
 Local está no armazenamento local de thread.  
  
 `LocIsRegRel`  
 Local é relativo ao registro.  
  
 `LocIsThisRel`  
 Local é `this`-relativo.  
  
 `LocIsEnregistered`  
 Local está em um registro.  
  
 `LocIsBitField`  
 Local está em um campo de bits.  
  
 `LocIsSlot`  
 Local é um slot Microsoft Intermediate Language (MSIL).  
  
 `LocIsIlRel`  
 Local é relativo ao MSIL.  
  
 `LocInMetaData`  
 Local está no metadados.  
  
 `LocIsConstant`  
 Local é um valor constante.  
  
 `LocTypeMax`  
 O número de tipos de localização nesta enumeração.  
  
## <a name="remarks"></a>Comentários  
 As propriedades disponíveis para o [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interface dependem do local do símbolo dentro do arquivo de imagem. Para obter mais informações, consulte [locais de símbolo](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Os valores nesta enumeração são retornados por uma chamada para o [: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md)