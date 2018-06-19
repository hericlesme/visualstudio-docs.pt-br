---
title: toLocaleString (Date) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641346"
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
Converte uma data em uma cadeia de caracteres usando a localidade atual ou especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. O objeto `Date` a ser convertido.  
  
 `locales`  
 Opcional. Uma matriz de cadeias de caracteres de localidade que contêm uma ou mais marcas de idioma ou localidade. Se você incluir mais de uma cadeia de caracteres de localidade, liste-as em ordem decrescente de prioridade para que a primeira entrada seja a localidade preferencial. Se você omitir esse parâmetro, a localidade padrão do tempo de execução JavaScript será usada.  
  
 `options`  
 Opcional. Um objeto que contém uma ou mais propriedades que especificam as opções de comparação.  
  
## <a name="remarks"></a>Comentários  
 A partir do Internet Explorer 11, `toLocaleString` usa `Intl.DateTimeFormat` internamente para fazer comparações, que adiciona suporte para o `locales` e `options` parâmetros. Para obter mais informações sobre esses parâmetros, consulte [intl. DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Os parâmetros `locales` e `options` não têm suporte em todos os modos de documento e versões do navegador. Para obter mais informações, consulte a seção Requisitos.  
  
 Quando você usa o `toLocaleString` no modo de documento padrão do Internet Explorer 10, nos modos de documento anteriores e no modo quirks:  
  
-   Ele retorna um `String` objeto que contém a data gravada em formato de tempo padrão da localidade atual.  
  
-   Para datas entre 1601 e 1999 D.C., a data é formatada de acordo com configurações regionais do painel de controle do usuário.  
  
> [!NOTE]
>  Se você omitir o `locales` parâmetro, use `toLocaleString` apenas para exibir os resultados para um usuário; nunca usá-lo para computar valores dentro de um script, porque o resultado retornado é específico do computador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `toLocaleString` com uma localidade especificada e opções de comparação.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Parâmetros `locales` e `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)