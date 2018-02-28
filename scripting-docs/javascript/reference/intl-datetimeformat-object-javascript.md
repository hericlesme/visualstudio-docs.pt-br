---
title: Objeto intl. DateTimeFormat (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="intldatetimeformat-object-javascript"></a>Objeto Intl.DateTimeFormat (JavaScript)
Formata a data e a hora específicas à localidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dateTimeFormatObj`  
 Necessário. O nome da variável para atribuir o `DateTimeFormat` do objeto.  
  
 `locales`  
 Opcional. Uma matriz de cadeias de caracteres de localidade que contêm uma ou mais marcas de idioma ou localidade. Se você incluir mais de uma cadeia de caracteres de localidade, liste-as em ordem decrescente de prioridade para que a primeira entrada seja a localidade preferencial. Se você omitir esse parâmetro, a localidade padrão do tempo de execução JavaScript será usada. Consulte a seção Comentários para obter mais informações.  
  
 `options`  
 Opcional. Um objeto que contém uma ou mais propriedades que especificam as opções de formatação para a data e hora. Consulte a seção de comentários para obter detalhes.  
  
## <a name="remarks"></a>Comentários  
 O `locales` parâmetro deve estar de acordo com [BCP 47](http://tools.ietf.org/html/rfc5646) marcas de idioma ou localidade, como "en-US" e "zh-CN". A marca pode incluir o idioma, região, país e variante. Para obter exemplos de marcas de idioma, consulte [Apêndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47. Para `DateTimeFormat`, você pode adicionar o **-u** submarca na cadeia de caracteres de localidade para incluir uma ou ambas das seguintes extensões Unicode:  
  
-   -nu para especificar uma extensão do sistema de numeração: *idioma*-*região*-u-nu -*numberingsystem*  
  
     onde *numberingsystem* pode ser um dos seguintes: árabe, arabext, bali, beng, deva, fullwide, gujr, especialista, hanidec, khmr, knda, laoo, latn, membro, mylm, mong, mymr, orya, tamldec, telu, tailandês, tibt.  
  
-   -ca para especificar um calendário: *idioma*-*região*-u-AC -*calendário*  
  
     onde *calendário* pode ser um dos seguintes: budista, chinês, japonês, islamicc, gregory, Islâmica.  
  
 O `options` parâmetro pode incluir as seguintes propriedades:  
  
|Propriedade|Descrição|Valores possíveis|Valor padrão|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Especifica o algoritmo de correspondência de localidade a ser usado.|"pesquisa", "o melhor ajuste"|"o melhor ajuste"|  
|`formatMatcher`|Especifica o algoritmo de correspondência de formato a ser usado.|"básico", "o melhor ajuste"|"o melhor ajuste"|  
|`hour12`|Especifica se deve usar um formato de 12 horas para horas.|`true`(para o formato de 12 horas), `false` (para o formato de 24 horas)||  
|`timeZone`|Especifica o fuso horário. No mínimo, sempre há suporte para "UTC".|Um valor de fuso horário como "UTC".|"UTC"|  
|`weekday`|Especifica a formatação do dia do semana.|"limitar", "pequeno", "longos."|indefinido|  
|`era`|Especifica a formatação da era.|"limitar", "pequeno", "comprimento"|indefinido|  
|`year`|Especifica a formatação do ano.|"2 dígitos", "numéricos"|indefinido ou "numérica"|  
|`month`|Especifica a formatação do mês.|"2-", "numérico dígitos", "restrito", "curto", "tempo"|indefinido ou "numérica"|  
|`day`|Especifica a formatação do dia.|"2 dígitos", "numéricos"|indefinido ou "numérica"|  
|`hour`|Especifica a formatação de hora.|"2 dígitos", "numéricos"|indefinido|  
|`minute`|Especifica a formatação de um minuto.|"2 dígitos", "numéricos"|indefinido|  
|`second`|Especifica a formatação da segunda.|"2 dígitos", "numéricos"|indefinido|  
|`timeZoneName`|Especifica a formatação do fuso horário. Não há suporte para esta propriedade atualmente.|"curto", "comprimento".|Não há suporte para esta propriedade atualmente.|  
  
 Os valores padrão para `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute`, e `second` são `undefined`. Se você não definir essas propriedades, formatação "numérico" é usado para `year`, `month`, e `day`.  
  
 Cada localidade deve oferecer suporte, no mínimo, os seguintes formatos:  
  
-   dia da semana, ano, mês, dia, hora, minuto, segundo  
  
-   dia da semana, ano, mês, dia  
  
-   ano, mês, dia  
  
-   ano, mês  
  
-   mês, dia  
  
-   hora, minuto, segundo  
  
-   hora, minuto  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `DateTimeFormat`.  
  
|||  
|-|-|  
|Propriedade|Descrição|  
|[construtor](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Especifica a função que cria um objeto de formatador de data/hora.|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|Retorna uma função que formata uma data específica de localidade, usando as configurações de formatador de data/hora.|  
|[protótipo](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Retorna uma referência ao protótipo para um formatador de data/hora.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `DateTimeFormat`.  
  
|||  
|-|-|  
|Método|Descrição|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Retorna um objeto que contém as propriedades e os valores do objeto formatador de data/hora.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o resultado de passar um objeto de data para `DateTimeFormat` usando diferentes localidades.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um `DateTimeFormat` objeto que especifica o dia da semana atual no formato longo usando a localidade árabe (Arábia Saudita), o calendário islâmico e o sistema de numeração de latino.  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [toLocaleString (Date)](../../javascript/reference/tolocalestring-date.md)   
 [Método toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [Método toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Objeto intl. collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Objeto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)