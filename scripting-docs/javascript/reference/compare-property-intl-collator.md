---
title: Comparar a propriedade (intl. collator) | Microsoft Docs
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
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="compare-property-intlcollator"></a>Propriedade compare (Intl.Collator)
Retorna uma função que compara duas cadeias de caracteres usando a ordem de classificação do agrupamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `collatorObj`  
 Necessário. O nome do `Collator` objeto a ser usado para a comparação.  
  
## <a name="remarks"></a>Comentários  
 A função retornada pelo `compare` propriedade leva dois argumentos: `x` e `y`e retorna o resultado de uma comparação específicas de localidade de `x` e `y` usando as opções especificadas no `Collator` objeto.  
  
 O resultado da comparação será:  
  
-   -1 se `x` é antes `y` na ordem de classificação.  
  
-   0 (zero) se `x` é igual a `y` na ordem de classificação.  
  
-   1 se `x` após `y` na ordem de classificação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um `Collator` de objeto e executa uma comparação.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Collator` objetos para classificar uma matriz. Este exemplo mostra as diferenças específicas da localidade.  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `Collator` objeto para pesquisar uma cadeia de caracteres.  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)