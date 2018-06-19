---
title: Método localeCompare (String) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639546"
---
# <a name="localecompare-method-string-javascript"></a>Método localeCompare (String) (JavaScript)
Determina se duas cadeias de caracteres são equivalentes na localidade atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `stringVar`  
 Necessário. A primeira cadeia de caracteres a ser comparada.  
  
 `stringExp`  
 Necessário. A segunda cadeia de caracteres a ser comparada.  
  
 `locales`  
 Opcional. Uma matriz de cadeias de caracteres de localidade que contêm uma ou mais marcas de idioma ou localidade. Se você incluir mais de uma cadeia de caracteres de localidade, liste-as em ordem decrescente de prioridade para que a primeira entrada seja a localidade preferencial. Se você omitir esse parâmetro, a localidade padrão do tempo de execução JavaScript será usada. Esse parâmetro deve estar de acordo com [BCP 47](http://tools.ietf.org/html/rfc5646) padrões, consulte o [objeto intl. collator](../../javascript/reference/intl-collator-object-javascript.md) para obter detalhes.  
  
 `options`  
 Opcional. Um objeto que contém uma ou mais propriedades que especificam as opções de comparação. Consulte o [objeto intl. collator](../../javascript/reference/intl-collator-object-javascript.md) para obter detalhes.  
  
## <a name="remarks"></a>Comentários  
 Para as cadeias de caracteres de comparação, você pode especificar `String` objetos ou literais de cadeia de caracteres.  
  
 A partir do Internet Explorer 11, `localeCompare` usa o `Intl.Collator` objeto internamente para fazer comparações, que adiciona suporte para o `locales` e `options` parâmetros. Para obter mais informações sobre esses parâmetros, consulte [intl. collator](../../javascript/reference/intl-collator-object-javascript.md) e [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Os parâmetros `locales` e `options` não têm suporte em todos os modos de documento e versões do navegador. Para obter mais informações, consulte a seção Requisitos.  
  
 O `localeCompare` método executa uma comparação de cadeia de caracteres sensíveis à localidade de `stringVar` e `stringExp` e retorna resultados de um dos seguintes, dependendo da ordem de classificação da localidade padrão do sistema:  
  
-   -1 se `stringVar` classifica antes de `stringExp`.  
  
-   + 1 se `stringVar` classifica após `stringExp`.  
  
-   0 (zero) se duas cadeias de caracteres são equivalentes.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar `localeCompare`.  
  
```JavaScript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar `localeCompare` com a localidade alemão (Alemanha).  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `localeCompare` com a localidade alemão (Alemanha) e uma extensão específica de localidade que especifica a ordem de classificação para os livros de telefone alemão. Este exemplo mostra as diferenças específicas da localidade.  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Parâmetros `locales` e `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método toLocaleString (Object)](../../javascript/reference/tolocalestring-method-object-javascript.md)