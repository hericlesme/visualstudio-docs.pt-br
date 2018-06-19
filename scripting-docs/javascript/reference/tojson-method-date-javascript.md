---
title: Método toJSON (Data) (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641286"
---
# <a name="tojson-method-date-javascript"></a>Método toJSON (data) (JavaScript)
Usado pelo [stringify](../../javascript/reference/json-stringify-function-javascript.md) método para permitir que a transformação de dados de um objeto de serialização (JSON JavaScript Object Notation).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectname`  
 Necessário. Um objeto para o qual JSON serialização é desejada.  
  
## <a name="remarks"></a>Comentários  
 O `toJSON` método é usado pelo `JSON.stringify` função. `JSON.stringify`serializa um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valor em texto JSON. Se um `toJSON` método é fornecido para `JSON.stringify`, o `toJSON` método é chamado quando `JSON.stringify` é chamado.  
  
 O `toJSON` método é um membro interno do [data](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto. Retorna uma cadeia de caracteres de formato ISO de data para o fuso horário UTC (indicado pelo sufixo Z).  
  
 Você pode substituir o `toJSON` método para o `Date` digite ou definir um `toJSON` método para outros tipos de objeto alcançar a transformação de dados para o tipo de objeto específico antes de serialização JSON.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `toJSON` método para serializar os valores de membro de cadeia de caracteres em maiusculas. O `toJSON` método é chamado quando `JSON.stringify` é chamado.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra como usar o `toJSON` método que é um membro interno do [data](../../javascript/reference/date-object-javascript.md) objeto.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**Aplica-se a:** [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto JSON](../../javascript/reference/json-object-javascript.md)   
 [Função JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Função JSON. stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Métodos JavaScript](../../javascript/reference/javascript-methods.md)