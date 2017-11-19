---
title: "Método Compile (Expressão Regular) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="compile-method-regular-expression-javascript"></a>Método compile (expressão regular) (JavaScript)
Compila uma expressão regular em um formato interno para execução mais rápida.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `rgExp`  
 Necessário. Uma instância de um **Expressão Regular** objeto. Pode ser um nome de variável ou um literal.  
  
 *padrão*  
 Necessário. Uma expressão de cadeia de caracteres que contém um padrão de expressão regular a ser compilado  
  
 `flags`  
 Opcional. Os sinalizadores disponíveis, que podem ser combinados, são:  
  
-   g (pesquisa global por todas as ocorrências de *padrão*)  
  
-   i (ignorar maiúsculas e minúsculas)  
  
-   m (pesquisa em várias linhas)  
  
## <a name="remarks"></a>Comentários  
 O **compilar** método converte *padrão* em um formato interno para execução mais rápida. Isso permite um uso mais eficiente de expressões regulares em loops, por exemplo. Uma expressão regular compilada acelera as coisas ao reutilizar a mesma expressão repetidamente. Nenhuma vantagem é obtida, no entanto, se a expressão regular é alterado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **compilar** método:  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Sintaxe de expressão regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)