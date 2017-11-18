---
title: "Lógica ou operador (|) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '||'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '|| operator'
- logical OR operator
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80c8e1bcae57e13642a0c77ae75c7c2aac58ace6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="logical-or-operator--javascript"></a>Operador OR lógico (||) (JavaScript)
Executa uma disjunção lógica em duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 || expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *Expression1*  
 Qualquer expressão.  
  
 *Expression2*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Se uma ou ambas as expressões são avaliadas como **True**, *resultados* é **True**. A tabela a seguir ilustra como *resultados* é determinado:  
  
|Se `expression1` é|E `expression2` é|O `result` é|  
|-------------------------|--------------------------|---------------------|  
|verdadeiro|verdadeiro|verdadeiro|  
|verdadeiro|False|verdadeiro|  
|False|verdadeiro|verdadeiro|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa as seguintes regras para converter valores não boolianos para valores booleanos:  
  
-   Todos os objetos são considerados como true.  
  
-   Cadeias de caracteres são consideradas falsas se e somente se elas estiverem vazias.  
  
-   `null`e são considerados false.  
  
-   Números são false se e somente se, eles são 0.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)