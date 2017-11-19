---
title: "Função eval (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="eval-function-javascript"></a>Função eval (JavaScript)
Avalia [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de código e o executa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `codeString`  
 Necessário. Um `String` valor contém válido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código.  
  
## <a name="remarks"></a>Comentários  
 O `eval` função permite a execução dinâmica de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código-fonte.  
  
 O `codeString` cadeia de caracteres é analisada pelo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] analisador e executado.  
  
 O código é passado para o `eval` função é executada no mesmo contexto de chamada para o `eval` função.  
  
 Sempre que possível, use o [função JSON Parse](../../javascript/reference/json-parse-function-javascript.md) desserializar em texto JSON JavaScript Object Notation (). O `JSON.parse` função é mais segura e executado mais rápido do que o `eval` função.  
  
## <a name="example"></a>Exemplo  
 O código a seguir inicializa a variável `myDate` em uma data de teste.  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto String](../../javascript/reference/string-object-javascript.md)