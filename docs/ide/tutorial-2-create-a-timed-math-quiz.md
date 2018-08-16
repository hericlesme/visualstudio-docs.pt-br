---
title: 'Tutorial 2: Criar um teste de matemática temporizado'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b28afd645351577073eb7525cf4bed321afb09c0
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008389"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Tutorial 2: Criar um teste de matemática temporizado

Neste tutorial, você cria um teste no qual o tomador de teste deve responder a quatro problemas aritméticos aleatórios dentro de um tempo especificado. Você aprenderá como:

-   Gere números aleatórios usando a classe de <xref:System.Random>.

-   Disparar eventos para que ocorram em um horário específico usando um controle de <xref:System.Windows.Forms.Timer>.

-   Fluxo do programa de controle usando instruções de `if else`.

-   Execute operações aritméticas básicas no código.

Quando você terminar, seu teste ficará parecido com a imagem a seguir, mas com números diferentes:

![Teste de matemática com quatro problemas](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Links do tutorial

Para baixar uma versão concluída do teste, veja [Exemplo de tutorial de teste completo de matemática](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

> [!NOTE]
> O Visual C# e o Visual Basic são abordados neste tutorial, por isso, concentre-se nas informações específicas da linguagem de programação que você está usando.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Etapa 1: Criar um projeto e adicionar rótulos ao formulário](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Comece criando o projeto, alterando propriedades e adicionando controles `Label`.|
|[Etapa 2: Criar um problema de adição aleatório](../ide/step-2-create-a-random-addition-problem.md)|Crie um problema de adição, e use a classe de `Random` para gerar números aleatórios.|
|[Etapa 3: Adicionar um temporizador de contagem regressiva](../ide/step-3-add-a-countdown-timer.md)|Adicione um timer de contagem regressiva de modo que o teste possa ser cronometrado.|
|[Etapa 4: Adicionar o método CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Adicione um método para verificar se o comprador de teste inseriu uma resposta correta para o problema.|
|[Etapa 5: Adicionar manipuladores de eventos Enter para os controles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Adicione manipuladores de eventos que facilitam a tomada do teste.|
|[Etapa 6: Adicionar um problema de subtração](../ide/step-6-add-a-subtraction-problem.md)|Adicione um problema de subtração que gerencia números aleatórios, usa o timer, e o verifica se as respostas estão corretas.|
|[Etapa 7: Adicionar problemas de multiplicação e divisão](../ide/step-7-add-multiplication-and-division-problems.md)|Adicione problemas de divisão e multiplicação que geram números aleatórios, usam o timer, e verificam se as respostas estão corretas.|
|[Etapa 8: Personalizar o teste](../ide/step-8-customize-the-quiz.md)|Tente outros recursos, como alterar cores e adicionar uma dica.|
