---
title: "Função Isview (ArrayBuffer) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aaae2acb38aa2f8c4b5e49ea203e86665315700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="arraybufferisview-function-arraybuffer"></a>Função ArrayBuffer.isView (ArrayBuffer)
Determina se um objeto fornece uma visão do buffer.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
ArrayBuffer.isView(object)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto a ser testado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se uma destas condições for verdadeira:  
  
-   `object` é um objeto `DataView`.  
  
-   `object` é uma matriz digitada.  
  
 Do contrário, o método retorna `false`.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o uso da função `isView` para testar uma matriz digitada e um objeto `DataView`.  
  
```JavaScript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)