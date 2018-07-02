---
title: 'DA0007: evitar usar exceções no fluxo de controle | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b7f673adc1c5f93c3cf356218c510cad7f8d229
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749860"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: evitar usar exceções no fluxo de controle
|||  
|-|-|  
|ID de regra|DA0007|  
|Categoria|Uso do .NET Framework|  
|Métodos de criação de perfil|Todos|  
|Mensagem|Um número elevado de exceções está sendo gerado de forma consistente. Considere a redução do uso de exceções na lógica do programa.|  
|Tipo de mensagem|Aviso|  
  
 Ao criar o perfil usando a amostragem, a memória do .NET ou métodos de contenção de recursos, é necessário coletar pelo menos 25 amostras para disparar essa regra.  
  
## <a name="cause"></a>Causa  
 Uma alta taxa de manipuladores de exceção do .NET Framework foram chamados nos dados de criação de perfil. Considere o uso de outra lógica de fluxo de controle para reduzir o número de exceções geradas.  
  
## <a name="rule-description"></a>Descrição da regra  
 Embora o uso de manipuladores de exceção para capturar erros e outros eventos que interrompem a execução do programa seja uma boa prática, o uso do manipulador de exceção como parte da lógica regular de execução do programa pode ser caro e deve ser evitado. Na maioria dos casos, as exceções devem ser usadas somente em circunstâncias que ocorrem com pouca frequência e que não são esperadas. Exceções não devem ser usadas para retornar valores como parte do fluxo típico do programa. Em muitos casos, é possível evitar acionar exceções validando valores e usando a lógica condicional para interromper a execução de instruções que causam o problema.  
  
 Para obter mais informações, confira a seção [Exception Management](http://go.microsoft.com/fwlink/?LinkID=177825) (Gerenciamento de exceções) de **Chapter 5 — Improving Managed Code Performance** (Capítulo 5 – Melhorando o desempenho de código gerenciado) no volume **Improving .NET Application Performance and Scalability** (Melhorando o desempenho e a escalabilidade de aplicativos .NET) na biblioteca **Microsoft Patterns and Practices** (Padrões e Práticas da Microsoft) no MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Como investigar um aviso  
 Clique duas vezes na mensagem da janela Lista de Erros para navegar para a exibição Marcas. Localize a coluna que contém as medições das **Exceções do .NET CLR (@ProcessInstance)\\nº de exceções geradas/segundos**. Determine se há fases específicas da execução do programa em que o tratamento de exceção é mais frequente do que em outras. Usando um perfil de amostragem, tente identificar instruções throw e blocos try/catch que geram exceções frequentes. Se necessário, adicione lógica para capturar blocos para ajudá-lo a entender quais exceções são tratadas com mais frequência. Sempre que possível, substitua instruções throw ou blocos catch frequentemente executados por uma lógica de controle de fluxo simples ou um código de validação.  
  
 Por exemplo, se você descobrir que seu aplicativo está tratando exceções DivideByZeroException frequentes, a adição de lógica ao programa para verificar se há denominadores com valores zero melhorará o desempenho do aplicativo.