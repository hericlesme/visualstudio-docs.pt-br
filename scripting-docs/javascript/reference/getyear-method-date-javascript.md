---
title: Método getYear (Date) (JavaScript) | Microsoft Docs
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
- getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637076"
---
# <a name="getyear-method-date-javascript"></a>Método getYear (Date) (JavaScript)
Obtém o ano de uma `Date` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o ano.  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
>  Esse método está obsoleto e é fornecido para compatibilidade com versões anteriores apenas. Use o método `getFullYear` em seu lugar.  
  
 Em [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]e, em seguida, no Internet Explorer versões começando com [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], o valor retornado é o ano armazenado menos 1900. Por exemplo, o ano 1899 é retornado como -1 e o ano 2000 é retornado como 100.  
  
 Em [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] por meio de [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], a fórmula depende do ano. Para os anos de 1900 a 1999, o valor retornado é um valor de 2 dígitos que é o ano armazenado menos 1900. Para datas fora do intervalo, o ano de 4 dígitos é retornado. Por exemplo, 1996 é retornado como 96, mas 1825 e 2025 são retornados como está.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Método getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Método setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Método setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [Método setYear (Date)](../../javascript/reference/setyear-method-date-javascript.md)