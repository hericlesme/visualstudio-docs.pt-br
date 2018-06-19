---
title: Método toLocaleUpperCase (String) (JavaScript) | Microsoft Docs
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
- toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640426"
---
# <a name="tolocaleuppercase-method-string-javascript"></a>Método toLocaleUpperCase (String) (JavaScript)
Retorna uma cadeia de caracteres em que todos os caracteres alfabéticos foram convertidos em maiusculas, sempre levando em conta o host localidade do ambiente atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `stringVar` referência é um `String` literal de cadeia de caracteres ou objeto.  
  
 O `toLocaleUpperCase` método converte os caracteres em uma cadeia de caracteres, levando em conta a localidade atual do ambiente de host. Na maioria dos casos, o resultado é o mesmo que o resultado de `toUpperCase` método. Os resultados diferentes se as regras para um idioma em conflito com os mapeamentos de casos Unicode regulares.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método toLocaleLowerCase (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Método toUpperCase (String)](../../javascript/reference/touppercase-method-string-javascript.md)