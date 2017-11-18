---
title: "Função parseInt (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="parseint-function-javascript"></a>Função parseInt (JavaScript)
Converte uma cadeia de caracteres em um inteiro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `numString`  
 Necessário. Uma cadeia de caracteres para converter em um número.  
  
 `radix`  
 Opcional. Um valor entre 2 e 36 que especifica a base do número em `numString`. Se esse argumento não for fornecido, cadeias de caracteres com o prefixo '0x' são consideradas hexadecimais. Todas as outras cadeias de caracteres são consideradas decimais.  
  
## <a name="remarks"></a>Comentários  
 O `parseInt` função retorna um valor inteiro igual ao número contido na `numString`. Se nenhum prefixo de `numString` pode ser analisado com êxito em um número inteiro, `NaN` (não um número) será retornado.  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Você pode testar `NaN` usando o `isNaN` função.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  A partir do [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], o `parseInt` função não trata uma cadeia de caracteres que tem um prefixo de '0' como um octal. Quando você não estiver usando o `parseInt` funcionar, no entanto, cadeias de caracteres com um prefixo de '0' ainda podem ser interpretadas como octals. Consulte [tipos de dados](../../javascript/data-types-javascript.md) para obter informações sobre inteiros octais.  
  
## <a name="see-also"></a>Consulte também  
 [Função isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Função parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)   
 [Método valueOf (Object)](../../javascript/reference/valueof-method-object-javascript.md)