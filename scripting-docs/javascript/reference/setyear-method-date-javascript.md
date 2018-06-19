---
title: Método setYear (Date) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640276"
---
# <a name="setyear-method-date-javascript"></a>Método setYear (Date) (JavaScript)
Define o valor de ano de `Date` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `dateObj`  
 Necessário. Qualquer objeto `Date`.  
  
 `numYear`  
 Necessário. Para os anos de 1900 a 1999, isso é um valor numérico igual ao ano menos 1900. Para datas fora do intervalo, isso é um valor numérico de 4 dígitos.  
  
## <a name="remarks"></a>Comentários  
 Esse método está obsoleto e é mantido para versões anteriores somente para compatibilidade. Use o método `setFullYear` em seu lugar.  
  
 Para definir o ano de uma `Date` objeto 1997, chamada **setYear(97)**. Para definir o ano 2010, chame **setYear(2010)**. Por fim, para definir o ano como um ano no intervalo 0-99, use o `setFullYear` método.  
  
> [!NOTE]
>  Para [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] versão 1.0, `setYear` usa um valor que é o resultado da adição de 1900 para o valor de ano fornecido pelo `numYear`, independentemente do valor do ano. Por exemplo, para definir o ano como 1899 `numYear` é -1 e para definir o ano 2000 `numYear` é 100.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Método getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Método getYear (Date)](../../javascript/reference/getyear-method-date-javascript.md)   
 [Método setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Método setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)