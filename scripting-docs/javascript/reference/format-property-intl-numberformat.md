---
title: formato de propriedade (intl. NumberFormat) | Microsoft Docs
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be40f8e94220ad7504dd3b9736e71b3416bb3d2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intlnumberformat"></a>Propriedade format (Intl.NumberFormat)
Retorna uma função que formata um número específico de localidade, usando as configurações de formatador de número especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `numberFormatObj`  
 Necessário. O nome do `NumberFormat` objeto a ser usado como um formatador.  
  
## <a name="remarks"></a>Comentários  
 A função retornada pelo `format` propriedade aceita um único argumento, `value`e retorna uma cadeia de caracteres que representa o número localizado usando as opções especificadas no `NumberFormat` objeto. Se `value` não for fornecido, a função retorna `NaN` (não um número).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `NumberFormat` objeto para criar um número localizado.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)