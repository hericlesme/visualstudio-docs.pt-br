---
title: "Função Date.Now (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="datenow-function-javascript"></a>Função Date.now (JavaScript)
Obtém a data e hora atuais.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>Valor de retorno  
 O número de milissegundos entre meia-noite de 1º de janeiro de 1970 e a data e hora atuais.  
  
## <a name="remarks"></a>Comentários  
 O [método getTime](../../javascript/reference/gettime-method-date-javascript.md) retorna o número de milissegundos entre 1º de janeiro de 1970 e uma data especificada.  
  
 Para obter informações sobre como calcular o tempo decorrido e comparar as datas, consulte [Calculando datas e horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `now`.  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>Requisitos  
 Não tem suporte em versões instaladas anteriores ao Internet Explorer 9. No entanto, há suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9, padrões do Internet Explorer 10. Com suporte também em [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos.  
  
## <a name="see-also"></a>Consulte também  
 [Método getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Objeto Date](../../javascript/reference/date-object-javascript.md)   
 [Calculando datas e horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Métodos JavaScript](../../javascript/reference/javascript-methods.md)