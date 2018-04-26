---
title: 'Erro: O processo de destino foi encerrado com código &#39;código&#39; ao avaliar a função &#39;função&#39; | Microsoft Docs'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5e9221ccf162180a89cc88b1ceebcf55be39eef
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Erro: O processo de destino foi encerrado com código &#39;código&#39; ao avaliar a função &#39;função&#39;

Mensagem de texto completo: O processo de destino foi encerrado com o código 'code' durante a avaliação da função 'function'.

Para tornar mais fácil inspecionar o estado dos objetos do .NET, o depurador automaticamente forçar o processo depurado para executar código adicional (normalmente métodos getter de propriedade e `ToString` funções). Na maioria dos cenários, essas funções concluída com êxito ou lançam exceções que podem ser capturadas pelo depurador. No entanto, há algumas situações em que as exceções não podem ser detectadas porque ultrapassar os limites de kernel, exigem bombeamento de mensagens do usuário ou são irrecuperáveis. Como resultado, um getter de propriedade ou método ToString que executa o código que explicitamente encerra o processo (por exemplo, chamadas de `ExitProcess()`) ou lança uma exceção sem tratamento que não pode ser capturada (por exemplo, `StackOverflowException`) terminará o processo depurado e término da sessão de depuração. Se você receber essa mensagem de erro, isso ocorreu.
 
Uma razão comum para esse problema é que, quando o depurador avalia uma propriedade que chama a mesmo, isso pode resultar em uma exceção de estouro de pilha. A exceção de estouro de pilha não pode ser recuperada e o processo de destino será encerrado.
 
## <a name="to-correct-this-error"></a>Para corrigir este erro
 
Há duas soluções possíveis para esse problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solução 1 #: Impedir que o depurador chamar a propriedade getter ou o método ToString 

A mensagem de erro informará o nome da função que o depurador tentou chamar. Com o nome da função, você pode tentar novamente avaliar essa função do **imediato** janela Depurar a avaliação. É possível depurar ao avaliar a partir o **imediato** janela porque, diferentemente implícita avaliações do **locais/Autos/inspecionar** windows, o depurador interrompe em exceções sem tratamento.

Se você pode modificar essa função, você pode impedir que o depurador chamar o getter de propriedade ou `ToString` método. Tente uma das seguintes opções:
 
* Altere o método para algum outro tipo de código, além de um getter de propriedade ou método ToString e o problema desaparecerá.
    -ou-
* (Para `ToString`) definir um `DebuggerDisplay` atributo no tipo e você pode ter o depurador avaliar algo diferente de `ToString`.
    -ou-
* (Para uma propriedade getter) Coloque o `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atributo na propriedade. Isso pode ser útil se você tiver um método que deve permanecer uma propriedade por razões de compatibilidade de API, mas realmente deve ser um método.

Se você não pode modificar este método, você poderá interromper o processo de destino em uma instrução alternativa e tente novamente a avaliação.
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>Solução #2: Desabilitar todos os avaliação implícita
 
Se as soluções anteriores não corrigir o problema, vá para **ferramentas** > **opções**e desmarque a configuração **depuração**  >   **Geral** > **habilitar avaliação de propriedades e outras chamadas de função implícitas**. Isso desabilitará a maioria das avaliações de função implícita e deve resolver o problema.



  
