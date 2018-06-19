---
title: Método (String) (JavaScript) endsWith | Microsoft Docs
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6d57d501f0f100f069522e4b51666918168fa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636336"
---
# <a name="endswith-method-string-javascript"></a>Método endsWith (Cadeia de caracteres) (JavaScript)
Retorna um valor que indica se uma cadeia de caracteres ou uma subcadeia de caracteres termina com outra cadeia de caracteres de especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O objeto de cadeia de caracteres a ser usado na pesquisa.  
  
 `str`  
 Necessário. A cadeia de caracteres de pesquisa.  
  
 `position`  
 Opcional. A posição do primeiro caractere a ser pesquisado com relação ao objeto de cadeia de caracteres, começando com 0.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o início da cadeia de caracteres em `position` terminar com a cadeia de caracteres de pesquisa, o método `endsWith` retornará `true`. Caso contrário, retornará `false`.  
  
## <a name="exceptions"></a>Exceções  
 Se `str` for um `RegExp`, um `TypeError` será lançado.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]