---
title: Objeto Error (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Error
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Error object
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc03f13a501a1a13a2e7f3eea000b406559f30b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="error-object-javascript"></a>Objeto Error (JavaScript)
Contém informações sobre erros.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `errorObj`  
 Obrigatório. O nome da variável à qual o objeto `Error` é atribuído. A atribuição de variável é omitida quando você cria o erro usando uma instrução `throw`.  
  
 `number`  
 Opcional. Valor numérico atribuído a um erro. Zero se for omitido.  
  
 `description`  
 Opcional. Cadeia de caracteres curta que descreve um erro. Cadeia de caracteres vazia, se omitida.  
  
## <a name="remarks"></a>Comentários  
 Sempre que ocorre um erro de tempo de execução, uma instância do objeto `Error` é criada para descrever esse erro. Essa instância possui duas propriedades intrínsecas que contêm a descrição do erro (propriedade `description`) e o número do erro (propriedade `number`). Para obter mais informações, consulte [erros de tempo de execução de JavaScript](../../javascript/reference/javascript-run-time-errors.md).  
  
 Um número de erro é um valor de 32 bits. A palavra de 16 bits superior é o código do recurso, enquanto que a palavra inferior é o código de erro propriamente dito.  
  
 Os objetos `Error` também podem ser criados explicitamente usando a sintaxe mostrada acima ou gerados com o uso da instrução `throw`. Em ambos os casos, é possível adicionar quaisquer propriedades que você escolher para expandir a capacidade do objeto `Error`.  
  
 Normalmente, a variável local é criada em uma **try... catch** instrução refere-se ao criadas implicitamente `Error` objeto. Como resultado, você pode usar o número e a descrição do erro de qualquer forma que escolher.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do objeto `Error`.  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do objeto `Error` criado implicitamente.  
  
```JavaScript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## <a name="methods"></a>Métodos  
 [Método toString (Error)](../../javascript/reference/tostring-method-error.md) &#124; [método valueOf (Date)](../../javascript/reference/valueof-method-date.md)  
  
## <a name="properties"></a>Propriedades  
 [Propriedade Constructor (erro)](../../javascript/reference/constructor-property-error.md) &#124; [propriedade description](../../javascript/reference/description-property-error-javascript.md) &#124; [propriedade message](../../javascript/reference/message-property-error-javascript.md) &#124; [propriedade name](../../javascript/reference/name-property-error-javascript.md) &#124; [propriedade número](../../javascript/reference/number-property-error-javascript.md) &#124; [propriedade prototype (erro)](../../javascript/reference/prototype-property-error.md) &#124; [propriedade stack (Error)](../../javascript/reference/stack-property-error-javascript.md) &#124; [stackTraceLimit propriedade (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Instrução throw](../../javascript/reference/throw-statement-javascript.md)   
 [Try...... finally instrução catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Instrução var](../../javascript/reference/var-statement-javascript.md)   
 [Aplicativo de exemplo de JavaScript Hilo (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)