---
title: formato de propriedade (intl. DateTimeFormat) | Microsoft Docs
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636586"
---
# <a name="format-property-intldatetimeformat"></a>Propriedade format (Intl.DateTimeFormat)
Retorna uma função que formata uma data específica de localidade, usando as configurações de formatador de data/hora especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dateTimeFormatObj`  
 Necessário. O nome do `DateTimeFormat` objeto a ser usado como um formatador.  
  
## <a name="remarks"></a>Comentários  
 A função retornada pelo `format` propriedade aceita um único argumento, `date`e retorna uma cadeia de caracteres que representa a data localizada usando as opções especificadas no `DateTimeFormat` objeto. O `date` parâmetro da função retornado deve ser um número, cadeia de caracteres de data, ou um `Date` objeto. Se `date` não for fornecido, a função usa [Date.now](../../javascript/reference/date-now-function-javascript.md) como o valor de entrada padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `DateTimeFormat` objeto para localizar a data "1 de dezembro de 2007" em alemão e reformatá-lo.  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)