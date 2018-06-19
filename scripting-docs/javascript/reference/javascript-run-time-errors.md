---
title: Erros de tempo de execução de JavaScript | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT-32725
- VS.WebClient.Help.SCRIPT7002
- VS.WebClient.Help.SCRIPT1001
- VS.WebClient.Help.SCRIPT16389
- VS.WebClient.HelpSCRIPT50
- VS.WebClient.HelpSCRIPT70
- VS.WebClient.HelpSCRIPT87
- VS.WebClient.HelpSCRIPT65535
- VS.WebClient.HelpSCRIPT445
- VS.WebClient.HelpSCRIPT600
- VS.WebClient.HelpSCRIPT2343
- VS.WebClient.HelpSCRIPT122
- VS.WebClient.HelpSCRIPT28
- VS.WebClient.HelpSCRIPT16386
- VS.WebClient.HelpSCRIPT7015
- VS.WebClient.HelpSCRIPT3
- VS.WebClient.HelpSCRIPT16388
- VS.WebClient.HelpSCRIPT14
- VS.WebClient.HelpSCRIPT12030
- VS.WebClient.HelpSCRIPT12029
- VS.WebClient.HelpSCRIPT1001
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- run-time errors, JavaScript
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb75c59fae32911c3dd3a7468439a198d7191755
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640796"
---
# <a name="javascript-run-time-errors"></a>JavaScript Erros de tempo de execução
Erros de tempo de execução do [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] são erros que ocorrem quando o script tenta executar uma ação que o sistema não pode executar. Esses erros podem ocorrer quando há expressões variáveis em avaliação ou quando a memória está sendo alocada.  
  
## <a name="windows-runtime-errors"></a>Erros de Tempo de Execução do Windows  
 Se você está usando APIs do Tempo de Execução do Windows no aplicativo [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], é possível que erros de JavaScript sejam convertidos de HRESULTs do Tempo de Execução do Windows. Os HRESULTs do Tempo de Execução do Windows acima do intervalo 0x80070000 são convertidos em erros de JavaScript, quando o valor hexadecimal dos bits baixos é convertido em valor decimal. Por exemplo, o HRESULT 0x80070032 é convertido no valor decimal 50 e o erro do JavaScript exibido é SCRIPT50. O HRESULT 0x80074005 é convertido no valor decimal 16389 e o erro do JavaScript exibido é SCRIPT16389.  
  
## <a name="errors"></a>Erros  
  
|Número do erro|Descrição|  
|------------------|-----------------|  
|5|[Acesso negado](../../javascript/misc/access-is-denied.md)|  
|438|[O objeto não dá suporte a essa propriedade ou método](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|Memória insuficiente|  
|5029|[O tamanho da matriz deve ser um número inteiro finito e positivo](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[O tamanho da matriz deve receber um número finito e positivo](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[Objeto de matriz ou argumentos esperado](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[Booliano esperado](../../javascript/misc/boolean-expected.md)|  
|5003|[Não é possível designar a um resultado de função](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[Não é possível designar a "isso"](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[Referência circular no argumento de valor não é compatível](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[Objeto de data esperado](../../javascript/misc/date-object-expected.md)|  
|5015|[Objeto enumerador esperado](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[Exceção lançada, mas não capturada](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[Esperado ')' na expressão regular](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[Esperado ' &#93;' na expressão regular](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[A função não tem um objeto de protótipo válido](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[Função esperada](../../javascript/misc/function-expected.md)|  
|5008|[Atribuição ilegal](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[Intervalo inválido no conjunto de caracteres](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[Argumento substituto inválido](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[Objeto do JavaScript esperado](../../javascript/misc/javascript-object-expected.md)|  
|5001|[Número esperado](../../javascript/misc/number-expected.md)|  
|5007|[Objeto esperado](../../javascript/misc/object-expected.md)|  
|5012|[Membro de objeto esperado](../../javascript/misc/object-member-expected.md)|  
|5016|[Objeto de expressão regular esperado](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[Cadeia de caracteres esperada](../../javascript/misc/string-expected.md)|  
|5017|[Erro de sintaxe em expressão regular](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[O número de dígitos fracionários está fora do intervalo](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[A precisão está fora do intervalo](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[O URI a ser decodificado não tem uma codificação válida](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[O URI a ser decodificado contém um caractere inválido](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[Identificador indefinido](../../javascript/misc/undefined-identifier.md)|  
|5018|[Quantificador inesperado](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[VBArray esperado](../../javascript/misc/vbarray-expected.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Erros de sintaxe JavaScript](../../javascript/reference/javascript-syntax-errors.md)