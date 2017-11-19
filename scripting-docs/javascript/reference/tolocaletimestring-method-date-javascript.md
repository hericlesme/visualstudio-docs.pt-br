---
title: "Método toLocaleTimeString (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleTimeString method
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77d8ee8fb6757b13da22a3cf3a59d28a105292cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaletimestring-method-date-javascript"></a>Método toLocaleTimeString (Date) (JavaScript)
Retorna a hora como um valor de cadeia de caracteres apropriado para a localidade atual do ambiente de host ou uma localidade específica.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Um objeto `Date`.  
  
 `locales`  
 Opcional. Uma matriz de cadeias de caracteres de localidade que contêm uma ou mais marcas de idioma ou localidade. Se você incluir mais de uma cadeia de caracteres de localidade, liste-as em ordem decrescente de prioridade para que a primeira entrada seja a localidade preferencial. Se você omitir esse parâmetro, a localidade padrão do tempo de execução JavaScript será usada.  
  
 `options`  
 Opcional. Um objeto que contém uma ou mais propriedades que especificam as opções de comparação.  
  
## <a name="remarks"></a>Comentários  
 Iniciando no Internet Explorer 11, o `toLocaleTimeString` usa `Intl.DateTimeFormat` internamente para formatar a hora, que adiciona suporte aos parâmetros `locales` e `options`. Para obter mais informações sobre esses parâmetros, consulte [intl. DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Os parâmetros `locales` e `options` não têm suporte em todos os modos de documento e versões do navegador. Para obter mais informações, consulte a seção Requisitos.  
  
 Quando você usa o `toLocaleTimeString` no modo de documento padrão do Internet Explorer 10, nos modos de documento anteriores e no modo quirks:  
  
-   Ele retorna um valor de cadeia de caracteres que contém a hora no fuso horário atual.  
  
-   A hora retornada está no formato padrão da localidade atual do ambiente de host.  
  
 Se você omitir o parâmetro `locales`, o valor retornado deste método não poderá ser usado em scripts, porque ele variará de um computador para outro. Neste cenário, use o método apenas para texto de formato exibido - nunca como parte de um cálculo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `toLocaleTimeString` com uma localidade especificada e opções de comparação.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Parâmetros `locales` e `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método toTimeString (Date)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [Método toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)