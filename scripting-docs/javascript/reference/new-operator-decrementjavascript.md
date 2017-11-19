---
title: Operador New (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="new-operator-javascript"></a>Operador new (JavaScript)
Cria um novo objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `constructor`  
 Necessário. O construtor do objeto. Os parênteses podem ser omitidos se o construtor não utiliza argumentos.  
  
 `arguments`  
 Opcional. Argumentos a serem passados para o novo construtor do objeto.  
  
## <a name="remarks"></a>Comentários  
 O `new` operador executa as seguintes tarefas:  
  
-   Ele cria um objeto sem associados.  
  
-   Ele chama o construtor para o objeto, transmitindo um ponteiro para o objeto recentemente criado como o `this` ponteiro.  
  
-   O construtor, em seguida, inicializa o objeto de acordo com os argumentos passados para o construtor.  
  
 Estes são exemplos de usos válidos do **novo** operador.  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../javascript/reference/function-statement-javascript.md)