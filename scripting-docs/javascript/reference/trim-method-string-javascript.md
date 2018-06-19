---
title: Método Trim (String) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640726"
---
# <a name="trim-method-string-javascript"></a>Método trim (String) (JavaScript)
Remove os espaços em branco inicial e final e também os caracteres de terminação de linha em uma cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. Um objeto `String` ou literal de cadeia de caracteres. Essa cadeia de caracteres não é modificada pelo método `trim`.  
  
## <a name="return-value"></a>Valor de retorno  
 A cadeia de caracteres original com caracteres de espaço em branco inicial e final e caracteres terminadores de linha removidos.  
  
## <a name="remarks"></a>Comentários  
 Os caracteres removidos incluem espaço, tabulação, avanço de página, retorno de carro e alimentação de linha. Consulte [caracteres especiais](../../javascript/advanced/special-characters-javascript.md) para obter uma lista abrangente de caracteres de terminação de linha e de espaço em branco.  
  
 Para obter um exemplo que mostra como implementar seu próprio método trim, consulte [protótipos e herança de protótipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `trim`.  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Caracteres especiais](../../javascript/advanced/special-characters-javascript.md)   
 [Objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)   
 [Aplicativo de exemplo de rolagem, movimento panorâmico e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)