---
title: "Função String.Raw (JavaScript) | Microsoft Docs"
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
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="stringraw-function-javascript"></a>Função String.raw (JavaScript)
Retorna o formulário de cadeia de caracteres bruta de uma cadeia de caracteres de modelo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `templateStr`  
 Necessário. A cadeia de caracteres do modelo.  
  
 `obj`  
 Necessário. Um objeto bem formado especificado usando a notação literal de objeto, como { raw: 'value' }.  
  
 `...substitutions`  
 Opcional. Uma matriz (uma [parâmetro rest](../../javascript/functions-javascript.md)) consiste em um ou mais valores de substituição.  
  
## <a name="remarks"></a>Comentários  
 O `String.raw` função destina-se ao uso com [cadeias de caracteres de modelo](../../javascript/advanced/template-strings-javascript.md). A cadeia de caracteres bruta incluirá todos os caracteres de escape e barras invertidas presentes na cadeia de caracteres.  
  
 Um erro será lançado se `obj` não for um objeto bem formado.  
  
## <a name="example"></a>Exemplo  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]