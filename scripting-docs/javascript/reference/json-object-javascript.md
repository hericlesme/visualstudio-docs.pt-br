---
title: Objeto JSON (JavaScript) | Microsoft Docs
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
- JSON
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JSON object
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5310132368f665c6734c469a67636d33a08858d4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="json-object-javascript"></a>Objeto JSON (JavaScript)
Um objeto intrínseco que fornece funções para converter valores [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de e para o formato JSON (JavaScript Object Notation). A função `JSON.stringify` serializa um valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] para o texto JSON. A função `JSON.parse` desserializa o texto JSON para produzir um valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
JSON.[method]  
  
```  
  
## <a name="parameters"></a>Parâmetros  
 `Method`  
 Obrigatório. Nome de um dos métodos do objeto `JSON`.  
  
## <a name="remarks"></a>Comentários  
 Não é possível criar um objeto `JSON` usando o operador `new`. Um erro ocorrerá se você tentar fazer isso. No entanto, você pode substituir ou modificar o objeto `JSON`.  
  
 O mecanismo de script cria o objeto `JSON` quando esse mecanismo é carregado. Seus métodos estão sempre disponíveis para o seu script.  
  
 Para usar o objeto `JSON` intrínseco, certifique-se de não substituí-lo por outro objeto `JSON` definido no seu script. Talvez seja necessário modificar instruções de script existentes que detectam a presença de um objeto `JSON` porque essas instruções serão avaliadas de maneira diferente. Isso é demonstrado no exemplo a seguir.  
  
```JavaScript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 No exemplo anterior, `!this.JSON` é avaliado como falso no [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)]. Portanto, o código dentro da instrução `if` não é executado.  
  
## <a name="functions"></a>Funções  
 [Função JSON.parse](../../javascript/reference/json-parse-function-javascript.md)  
  
 [Função JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método toJSON (Data)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Objetos JavaScript](../../javascript/reference/javascript-objects.md)   
 [Aplicativo de exemplo do modelo hub (Windows Store)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)