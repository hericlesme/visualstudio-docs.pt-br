---
title: Bit a bit operador (~) (JavaScript) | Microsoft Docs
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
- "~"
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634256"
---
# <a name="bitwise-not-operator--javascript"></a>Operador NOT bit a bit (~) (JavaScript)
Executa um NOT (negação) bit a bit em uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *expressão*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Todos os operadores unários, como o `~` operador, avalia as expressões da seguinte maneira:  
  
-   Se aplicado a indefinido ou `null` expressões, um erro de tempo de execução é gerado.  
  
-   Os objetos são convertidos em cadeias de caracteres.  
  
-   Cadeias de caracteres são convertidas em números, se possível. Caso contrário, será gerado um erro de tempo de execução.  
  
-   Valores boolianos são tratados como números (0 se for false, 1 se for true).  
  
 O operador é aplicado para o número resultante.  
  
 O `~` operador examina a representação binária dos valores da expressão e faz uma operação de negação bit a bit nele.  
  
 Qualquer dígito que é um 1 na expressão se torna um 0 no resultado. Qualquer dígito que é 0 na expressão se torna um 1 no resultado.  
  
 O exemplo a seguir ilustra o uso de bit a bit (~) o operador NOT.  
  
```  
var temp = ~5;  
```  
  
 O valor resultante é -6, conforme mostrado na tabela a seguir.  
  
|Expressão|Valor binário (dois complemento)|Valor decimal|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Lógica operador NOT (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)