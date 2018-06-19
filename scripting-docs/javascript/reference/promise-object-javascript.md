---
title: Promessa de objeto (JavaScript) | Microsoft Docs
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
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61e5611dd0d455c7e7b704777cc2341ca43a2404
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640626"
---
# <a name="promise-object-javascript"></a>Objeto Promise (JavaScript)
Fornece um mecanismo para agendar o trabalho a ser feito em um valor que ainda não foi calculado. É uma abstração para gerenciar interações com APIs assíncronas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `promise`  
 Necessário. O nome da variável à qual a promessa é atribuída.  
  
 `resolve`  
 Necessário. Uma função que é executada para indicar que a promessa foi concluída com êxito.  
  
 `reject`  
 Opcional. Uma função que é executada para indicar que a promessa foi rejeitada com um erro.  
  
## <a name="remarks"></a>Comentários  
 Uma promessa deve ser concluída com um valor ou rejeitada com um motivo. O método `then` do objeto Promise é executado quando a promessa é concluída ou rejeitada, o que ocorrer primeiro. Se a promessa for concluída com êxito, a função de processamento de cumprimento do método `then` é executada. Se a promessa for rejeitada, a função de processamento de erro do método `then` (ou o método `catch`) é executada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como chamar uma função (`timeout`) que retorna uma promessa. O processador de cumprimento do método `then` é executado após o tempo limite de 5000 ms expirar.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="example"></a>Exemplo  
 Também é possível encadear chamadas para o método `then` conforme mostrado no código a seguir. Cada processador de conclusão em si deve retornar uma promessa para dar suporte ao encadeamento. Nesse código, que chama a mesma função `timeout`, a primeira chamada para o tempo limite é retornada após 1000 ms. O primeiro processador de conclusão chama `timeout` novamente, e a promessa retorna após 2000 ms. O processador de conclusão, em seguida, gera um erro. O processador de erro chama `Promise.all`, que retorna somente quando as duas chamadas para o tempo limite forem concluídas ou rejeitadas.  
  
```JavaScript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="functions"></a>Funções  
 A tabela a seguir descreve a função do objeto `Promise`.  
  
|Função|Descrição|  
|--------------|-----------------|  
|[Função Promise.All](../../javascript/reference/promise-all-function-promise.md)|Une duas ou mais promessas e retorna somente quando todas as promessas especificadas são concluídas ou rejeitadas.|  
|[Função Promise Race](../../javascript/reference/promise-race-function-promise.md)|Cria uma nova promessa que será resolvida ou rejeitada com o mesmo valor de resultado que a primeira promessa a ser resolvida ou rejeitada entre os argumentos passados.|  
|[Função Promise Reject](../../javascript/reference/promise-reject-function-promise.md)|Cria uma nova promessa rejeitada com resultado igual ao argumento passado.|  
|[Função Promise.](../../javascript/reference/promise-resolve-function-promise.md)|Cria uma nova promessa resolvida com resultado igual ao seu argumento.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir descreve os métodos do objeto `Promise`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Catch](../../javascript/reference/catch-method-promise.md)|Permite que você especifique o trabalho a ser realizado mediante a rejeição de uma promessa.|  
|[em seguida, método](../../javascript/reference/then-method-promise.md)|Permite que você especifique o trabalho a ser realizado mediante o cumprimento de uma promessa.|