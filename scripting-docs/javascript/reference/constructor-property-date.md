---
title: Propriedade Constructor (Data) | Microsoft Docs
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 798064117e17ee5b2988396de3c6545917373b10
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-date"></a>Propriedade constructor (Data)
Especifica a função que cria uma data.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
date.constructor  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `date` é o nome de um objeto de data.  
  
 A propriedade `constructor` é um membro do protótipo de cada objeto que tenha um protótipo. A propriedade `constructor` contém uma referência para a função que constrói instâncias daquele objeto específico.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da propriedade de construtor.  
  
```JavaScript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]