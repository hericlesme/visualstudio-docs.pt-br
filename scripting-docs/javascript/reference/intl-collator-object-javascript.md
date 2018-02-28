---
title: Objeto intl. collator (JavaScript) | Microsoft Docs
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
- Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="intlcollator-object-javascript"></a>Objeto Intl.Collator (JavaScript)
Compara cadeias de caracteres específicas à localidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `collatorObj`  
 Necessário. O nome da variável para atribuir o `Collator` do objeto.  
  
 `locales`  
 Opcional. Uma matriz de cadeias de caracteres de localidade que contêm uma ou mais marcas de idioma ou localidade. Se você incluir mais de uma cadeia de caracteres de localidade, liste-as em ordem decrescente de prioridade para que a primeira entrada seja a localidade preferencial. Se você omitir esse parâmetro, a localidade padrão do tempo de execução JavaScript será usada. Consulte a seção Comentários para obter mais informações.  
  
 `options`  
 Opcional. Um objeto que contém uma ou mais propriedades que especificam as opções de comparação. Consulte a seção de comentários para obter detalhes.  
  
## <a name="remarks"></a>Comentários  
 O `locales` parâmetro deve estar de acordo com [BCP 47](http://tools.ietf.org/html/rfc5646) marcas de idioma ou localidade, como "en-US" e "zh-CN-Hans". A marca pode incluir o idioma, região, país e variante. Para obter uma lista de idiomas, consulte o [registro de submarca IANA idioma](http://go.microsoft.com/fwlink/p/?linkid=227303). Para obter exemplos de marcas de idioma, consulte [Apêndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47. Para `Collator`, você pode incluir a extensão -u na cadeia de caracteres de localidade para especificar uma ou mais das seguintes extensões Unicode:  
  
-   co - para especificar agrupamentos variantes (específicas da localidade): "*idioma*-*região*-u-co -*valor*".  
  
-   -kn para especificar uma comparação numérica: "*idioma*-*região*- u-kn-true &#124; false".  
  
-   -kf para especificar se deseja classificar caracteres maiusculos ou minúsculos primeiro: "*idioma*-*região*- u-kf-superior &#124; inferior &#124; false"). Atualmente, não há suporte para essa extensão.  
  
 Para especificar uma comparação numérica, você pode definir a extensão de -kn na cadeia de caracteres de localidade ou usar o `numeric` propriedade o `options` parâmetro. Se você estiver usando o `numeric` propriedade, o valor de -kn não se aplicará.  
  
 O `options` parâmetro pode incluir as seguintes propriedades:  
  
-   `localeMatcher`. Especifica o algoritmo de correspondência de localidade a ser usado. Os valores possíveis são "pesquisa" e "o melhor ajuste". O valor padrão é "melhor ajuste".  
  
-   `usage`. Especifica se a meta de comparação de classificação ou pesquisa. Os valores possíveis são "Classificar" e "Pesquisar". O valor padrão é "Classificar".  
  
-   `sensitivity`. Especifica a sensibilidade do agrupamento. Os valores possíveis são "base", "ênfase", "case" e "variant". O valor padrão é `undefined`.  
  
-   `ignorePunctuation`. Especifica se a pontuação é ignorada na comparação. Os valores possíveis são "true" e "false". O valor padrão é `false`.  
  
-   `numeric`. Especifica se a classificação numérica é usada. Os valores possíveis são "true" e "false". O valor padrão é `false`.  
  
-   `caseFirst`. Não há suporte no momento.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `Collator`.  
  
|||  
|-|-|  
|Propriedade|Descrição|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Retorna uma função que compara duas cadeias de caracteres usando a ordem de classificação do agrupamento.|  
|[construtor](../../javascript/reference/constructor-property-intl-collator.md)|Especifica a função que cria um agrupamento.|  
|[protótipo](../../javascript/reference/prototype-property-intl-collator.md)|Retorna uma referência ao protótipo para um agrupamento.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Collator`.  
  
|||  
|-|-|  
|Método|Descrição|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Retorna um objeto que contém as propriedades e os valores de agrupamento.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um `Collator` de objeto e executa uma comparação.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
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
 O exemplo a seguir usa um `Collator` para pesquisar uma cadeia de caracteres do objeto e especifica opções de comparação.  
  
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
 [Método localeCompare (String)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Objeto intl. DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Objeto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)