---
title: Objeto intl. NumberFormat (JavaScript) | Microsoft Docs
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
- NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Objeto Intl.NumberFormat (JavaScript)
Formata o número específico à localidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `numberFormatObj`  
 Necessário. O nome da variável para atribuir o `NumberFormat` do objeto.  
  
 `locales`  
 Opcional. Uma matriz de cadeias de caracteres de localidade que contêm uma ou mais marcas de idioma ou localidade. Se você incluir mais de uma cadeia de caracteres de localidade, liste-as em ordem decrescente de prioridade para que a primeira entrada seja a localidade preferencial. Se você omitir esse parâmetro, a localidade padrão do tempo de execução JavaScript será usada. Consulte a seção Comentários para obter mais informações.  
  
 `options`  
 Opcional. Um objeto que contém uma ou mais propriedades que especificam as opções de formatação numéricas. Consulte a seção de comentários para obter detalhes.  
  
## <a name="remarks"></a>Comentários  
 O `locales` parâmetro deve estar de acordo com [BCP 47](http://tools.ietf.org/html/rfc5646) marcas de idioma ou localidade, como "en-US" e "zh-CN". A marca pode incluir o idioma, região, país e variante. Para obter exemplos de marcas de idioma, consulte [Apêndice A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47. Para `NumberFormat`, você pode adicionar o **-u** submarca seguido - nu para especificar uma extensão do sistema de numeração:  
  
 "*idioma*-*região*-u-nu -*numberingsystem*"  
  
 onde *numberingsystem* pode ser um dos seguintes: árabe, arabext, bali, beng, deva, fullwide, gujr, especialista, hanidec, khmr, knda, laoo, latn, membro, mylm, mong, mymr, orya, tamldec, telu, tailandês, tibt.  
  
 O `options` parâmetro pode incluir as seguintes propriedades:  
  
|Propriedade|Descrição|Valores possíveis|Valor padrão|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Especifica o algoritmo de correspondência de localidade a ser usado.|"pesquisa", "o melhor ajuste"|"o melhor ajuste"|  
|`style`|Especifica o estilo de formato de número.|"decimal", "porcentagem", "moeda"|"decimal"|  
|`currency`|Especifica o valor de moeda ISO 4217 como um código alfabético. Se o `style` está definido para "moeda", esse valor é necessário.|Consulte o ISO [lista de código de moeda e fundos](http://www.currency-iso.org/en/home/tables/table-a1.html).|indefinido|  
|`currencyDisplay`|Especifica se deve exibir a moeda como um código de moeda alfabético 4217 ISO, um símbolo de moeda localizada ou um nome de moeda localizada. Esse valor é usado somente se `style` é definida como "moeda".|"código", "símbolo", "name"|"símbolo de|  
|`useGrouping`|Especifica se um separador de agrupamento deve ser usado.|verdadeiro, FALSO|`true`.|  
|`minimumIntegerDigits`|Especifica o número mínimo de dígitos integrais para usar.|1 a 21.|21|  
|`minimumFractionDigits`|. Especifica o número mínimo de dígitos fracionários a ser usado.|0 a 20.|0|  
|`maximumFractionDigits`|Especifica o número máximo de dígitos fracionários a ser usado.|Esse valor pode variar de `minimumFractionDigits` a 20.|20.|  
|`minimumSignificantDigits`|Especifica o número mínimo de dígitos fracionários a ser mostrado.|Esse valor pode variar de 1 a 21.|1|  
|`maximumSignificantDigits`|Especifica o número máximo de dígitos fracionários a ser mostrado.|Esse valor pode variar de `minimumSignificantDigits` como 21.|21|  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `NumberFormat`.  
  
|||  
|-|-|  
|Propriedade|Descrição|  
|[construtor](../../javascript/reference/constructor-property-intl-numberformat.md)|Especifica a função que cria um objeto de número de formatador.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Retorna uma função que formata um número, usando as configurações de formatador número.|  
|[protótipo](../../javascript/reference/prototype-property-intl-numberformat.md)|Retorna uma referência ao protótipo para um formatador de número.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `NumberFormat`.  
  
|||  
|-|-|  
|Método|Descrição|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Retorna um objeto que contém as propriedades e os valores do objeto formatador número.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um `NumberFormat` objeto para a localidade en-US, com as opções de formatação especificadas.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram o resultado do uso de várias localidades diferentes e opções.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [toLocaleString (número)](../../javascript/reference/tolocalestring-number.md)   
 [Objeto intl. collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Objeto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)