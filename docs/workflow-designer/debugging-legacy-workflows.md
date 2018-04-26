---
title: Designer de fluxo de trabalho - depuração de fluxos de trabalho herdados
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33a8358c5d62b938fc64d608c9b4546ab1745aaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="debugging-legacy-workflows"></a>Depurando fluxos de trabalho herdados

Se você estiver usando o Designer de fluxo de trabalho herdado do Windows no Visual Studio para criar aplicativos do Windows Workflow Foundation (WF) que target.NET Framework 3.0 ou 3.5, você pode depurar seus fluxos de trabalho como qualquer outro programa, definindo pontos de interrupção, anexando a processos e examinando threads e a pilha de chamadas. Você também tem a opção de depurar remotamente.

> [!NOTE]
> Se várias versões do Visual Studio tiverem sido instaladas e desinstaladas no computador, a depuração do WF3 poderá falhar com uma das duas possibilidades a seguir:
>
> -   Os pontos de interrupção não foram atingidos.
> -   A seguinte mensagem é exibida:
>
> **Não é possível iniciar a depuração no servidor web. O depurador não está instalado corretamente.  Não é possível depurar o tipo de código solicitado.  Execute a instalação para instalar ou reparar o depurador.**
>
> Se qualquer um desses cenários ocorrer durante a depuração de fluxos de trabalho do .NET Framework 3.0 ou 3.5, execute um reparo da instalação do Visual Studio.

 O Windows Workflow Foundation integra-se com as seguintes janelas de depuração padrão do Visual Studio:

-   **Ponto de interrupção**: funciona conforme o esperado, mas você especifica uma atividade para o nome da função.

-   **Pilha de chamadas**: modificada para fornecer uma estrutura de tópicos de atividades que foram executadas em uma instância de fluxo de trabalho. As entradas na **pilha de chamadas** janela são uma pesquisa de profundidade das atividades em execução. Você pode clicar duas vezes em uma entrada para colocar o foco na atividade selecionada.

-   **Threads**: fornece a ID de instância da instância do fluxo de trabalho que está sendo depurada.

 O Visual Studio para Windows Foundation Workflow não oferece suporte aos seguintes recursos de depuração:

-   Pontos de interrupção condicionais na superfície do designer.

-   QuickWatch.

-   Definir próxima instrução.

-   Executar até o cursor.

-   Editar e continuar.

-   Depuração just-in-time.

-   Depuração de modo misto.