---
title: 'Erro: A avaliação da função &#39;função&#39; expirou e precisa ser interrompida de forma não segura | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9843dd870521312f45353c894908130fba0074c7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Erro: A avaliação da função &#39;função&#39; expirou e precisa ser interrompida de forma não segura

Mensagem de texto completo: avaliação da função 'function' atingiu o tempo limite e precisa ser interrompida de forma não segura. Isso pode ter corrompido o processo de destino. 

Para tornar mais fácil inspecionar o estado dos objetos do .NET, o depurador automaticamente forçará o processo depurado para executar código adicional (normalmente métodos getter de propriedade e ToString funções). Na maioria dos cenários de todas essas funções concluir rapidamente e facilitar a depuração muito. No entanto, o depurador não executa o aplicativo em uma área restrita. Como resultado, um getter de propriedade ou método ToString que chama uma função nativa trava pode resultar em tempos limite de tempo que pode não ser recuperável. Se você receber essa mensagem de erro, isso ocorreu.
 
Uma razão comum para esse problema é que quando o depurador avalia uma propriedade, ela só permita que o thread está sendo inspecionado para executar. Portanto, se a propriedade estiver esperando em outros threads para execução dentro do aplicativo depurado e está aguardando de forma que o tempo de execução do .NET não é capaz de interrupção, esse problema ocorrerá.
 
## <a name="to-correct-this-error"></a>Para corrigir este erro
 
Há três possíveis soluções para esse problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solução 1 #: Impedir que o depurador chamar a propriedade getter ou o método ToString
 
A mensagem de erro informará o nome da função que o depurador tentou chamar. Se você pode modificar essa função, você pode impedir que o depurador ao chamar o getter de propriedade ou método ToString. Tente uma das seguintes opções:
 
* Altere o método para algum outro tipo de código, além de um getter de propriedade ou método ToString e o problema desaparecerá.
    -ou-
* (Para ToString) Definir um atributo DebuggerDisplay no tipo e você pode fazer com que o depurador avaliar algo diferente de ToString.
    -ou-
* (Para uma propriedade getter) Coloque o `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atributo na propriedade. Isso pode ser útil se você tiver um método que deve manter uma propriedade por razões de compatibilidade de API, mas realmente deve ser um método.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Solução #2: Tem o código de destino peça o depurador para anular a avaliação
 
A mensagem de erro informará o nome da função que o depurador tentou chamar. Se o getter de propriedade ou método ToString pode falha ser executado corretamente, especialmente em situações em que o problema é que o código precisa outro thread para executar código e pode chamar a função de implementação `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` para solicitar que o depurador para anular a função avaliação. Com essa solução, ainda é possível avaliar explicitamente essas funções, mas o comportamento padrão é que a execução é interrompida quando ocorre a chamada de NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Solução #3: Desabilitar todos os avaliação implícita
 
Se as soluções anteriores não corrigir o problema, vá para *ferramentas* > *opções*e desmarque a configuração *depuração*  >   *Geral* > *habilitar avaliação de propriedades e outras chamadas de função implícitas*. Isso desabilitará a maioria das avaliações de função implícita e deve resolver o problema.



  
