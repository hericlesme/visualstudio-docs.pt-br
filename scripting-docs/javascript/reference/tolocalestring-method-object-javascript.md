---
title: "Método toLocaleString (Object) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>Método toLocaleString (Object) (JavaScript)
Retorna uma data é convertido em uma cadeia de caracteres usando a localidade atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `dateObj` é qualquer `Date` objeto.  
  
 O `toLocaleString` método retorna um `String` objeto que contém a data gravada em formato de tempo padrão da localidade atual.  
  
-   Para datas entre 1601 e 1999 D.C., a data é formatada de acordo com configurações regionais do painel de controle do usuário.  
  
-   Para datas fora desse intervalo, o formato padrão da **toString** método é usado.  
  
 Por exemplo, nos Estados Unidos, `toLocaleString` retorna "01/05/96 00:00:00" para 5 de janeiro. Na Europa, ele retorna "01/05/96 00:00:00" para a mesma data, como convenção Europeia coloca o dia antes do mês.  
  
> [!NOTE]
>  `toLocaleString`só deve ser usado para exibir os resultados ao usuário. ele deve nunca ser usado como base para a computação dentro de um script como o resultado retornado é específico do computador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de matriz](../../javascript/reference/array-object-javascript.md)&#124; [Data objeto](../../javascript/reference/date-object-javascript.md)&#124; [Número objeto](../../javascript/reference/number-object-javascript.md)&#124; [Objeto Object](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)