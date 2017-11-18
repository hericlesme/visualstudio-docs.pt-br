---
title: construtor propriedade (String) | Microsoft Docs
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1942073a9950a77c7e0cae759a9653318d8a18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-string"></a>Propriedade constructor (Cadeia de Caracteres)
Especifica a função que cria uma cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
string.constructor  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `string` é o nome de uma cadeia de caracteres.  
  
 A propriedade `constructor` é um membro do protótipo de cada objeto que tenha um protótipo. Isso inclui todos os intrínseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos exceto o `Global` e `Math` objetos. A propriedade `constructor` contém uma referência para a função que constrói instâncias daquele objeto específico.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da propriedade de construtor.  
  
```JavaScript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]