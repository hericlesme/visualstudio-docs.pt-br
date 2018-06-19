---
title: toLocaleString (número) | Microsoft Docs
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640826"
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
Converte um número em uma cadeia de caracteres usando a localidade atual ou especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `numberObj`  
 Necessário. O objeto `Number` a ser convertido.  
  
 `locales`  
 Opcional. Uma matriz de cadeias de caracteres de localidade que contêm uma ou mais marcas de idioma ou localidade. Se você incluir mais de uma cadeia de caracteres de localidade, liste-as em ordem decrescente de prioridade para que a primeira entrada seja a localidade preferencial. Se você omitir esse parâmetro, a localidade padrão do tempo de execução JavaScript será usada.  
  
 `options`  
 Opcional. Um objeto que contém uma ou mais propriedades que especificam as opções de comparação.  
  
## <a name="remarks"></a>Comentários  
 A partir do Internet Explorer 11, `toLocaleString` usa `Intl.NumberFormat` internamente para fazer comparações, que adiciona suporte para o `locales` e `options` parâmetros. Para obter mais informações sobre esses parâmetros, consulte [intl. NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Os parâmetros `locales` e `options` não têm suporte em todos os modos de documento e versões do navegador. Para obter mais informações, consulte a seção Requisitos.  
  
> [!NOTE]
>  Se você omitir o `locales` parâmetro, use `toLocaleString` apenas para exibir os resultados para um usuário, nunca use para computar valores dentro de um script, porque o resultado retornado é específico do computador (o método retornará a localidade atual).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `toLocaleString` método sem parâmetros.  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `toLocaleString` com uma localidade especificada e opções de comparação.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Parâmetros `locales` e `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)