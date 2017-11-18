---
title: "Método Fill (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4546bafb3fa3a8c242b8b7ef4ef2863ea86bf179
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="fill-method-array-javascript"></a>Método fill (Array) (JavaScript)
Preenche uma matriz com um valor especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. O objeto de matriz.  
  
 `value`  
 Necessário. O valor usado para preencher a matriz.  
  
 `start`  
 Opcional. O índice inicial usado para preencher os valores da matriz. O valor padrão é 0.  
  
 `end`  
 Opcional. O índice final usado para preencher os valores da matriz. O valor padrão é a propriedade length do objeto `this`.  
  
## <a name="remarks"></a>Comentários  
 Se `start` for negativo, `start` é tratado como `length` + `start`, onde `length` é o comprimento da matriz. Se `end` for negativo, `end` é tratado como `length` + `end`.  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir preenchem uma matriz com valores.  
  
```JavaScript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]