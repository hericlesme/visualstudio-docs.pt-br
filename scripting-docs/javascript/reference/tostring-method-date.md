---
title: "Método toString (Date) | Microsoft Docs"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-date"></a>Método toString (Date)
Retorna uma representação de cadeia de caracteres de uma data. O formato da cadeia de caracteres depende da localidade. Para os EUA Inglês (en-us), ele é o seguinte:  
  
 *dia da semana* *mês* *dia* *hora*: *minuto*:*segundo* *fuso horário* *ano*  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>Parâmetros  
 `date`  
 Necessário. A data para representar como uma cadeia de caracteres.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna a representação de cadeia de caracteres da data.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `toString` método com uma data.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]