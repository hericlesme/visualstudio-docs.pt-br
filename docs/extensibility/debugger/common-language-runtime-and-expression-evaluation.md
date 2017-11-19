---
title: "Common Language Runtime e avaliação de expressão | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba9a9a6b406ad5a94cced7820e6b4581db56eb2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime e avaliação de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compiladores, como Visual Basic e c# (pronunciado C-sharp), que o tempo de execução de linguagem comum (CLR) de destino, produzem MSIL Microsoft Intermediate Language (), que é posterior compilados para código nativo. O CLR fornece um mecanismo de depuração (DE) para depurar o código resultante. Se você pretende integrar a linguagem de programação proprietária IDE do Visual Studio, você pode optar por compilados para MSIL e, portanto, não precisa escrever sua próprias DE. No entanto, você terá que gravar um avaliador de expressão (EE) que é capaz de avaliar expressões dentro do contexto de sua linguagem de programação.  
  
## <a name="discussion"></a>Discussão  
 Expressões de idioma do computador geralmente são analisadas para produzir um conjunto de objetos de dados e um conjunto de operadores usados para manipulá-los. Por exemplo, a expressão "A + B" pode ser analisado para aplicar o operador de adição (+) para os dados de objetos "A" e "B", possivelmente resultando em outro objeto de dados. O conjunto total de objetos de dados, operadores e suas associações geralmente são representados em um programa como uma árvore, com os operadores em nós da árvore e os objetos de dados em ramificações. Uma expressão que é dividida em forma de árvore é geralmente chamada de uma árvore analisada.  
  
 Depois que uma expressão foi analisada, um provedor de símbolo (SP) é chamado para avaliar cada objeto de dados. Por exemplo, se "A" é definida em mais de um método e, em seguida, a pergunta "Quais A?" deve ser atendida antes que o valor de um pode ser determinado. A resposta retornada pelo SP é algo como "O terceiro item no quadro de pilhas quinto" ou "O A 50 bytes além do início da memória estática é alocado para este método."  
  
 Além de produzir MSIL para o próprio programa, compiladores CLR também podem produzir as informações de depuração muito descritivas que são gravadas em um arquivo de banco de dados do programa (. PDB). Desde que um compilador de linguagem proprietários gera informações de depuração no mesmo formato que os compiladores do CLR, SP do CLR é capaz de identificar da linguagem chamado objetos de dados. Depois que um objeto de dados nomeado foi identificado, o EE usa um objeto de fichário para associar (ou associar) o objeto de dados para a área de memória que contém o valor do objeto. O DE, em seguida, pode obter ou definir um novo valor para o objeto de dados.  
  
 Um compilador proprietário pode fornecer o CLR as informações de depuração chamando o `ISymbolWriter` interface (que é definida no .NET Framework no namespace `System.Diagnostics.SymbolStore`). Compilação para MSIL e gravar informações de depuração através dessas interfaces, um compilador proprietário pode usar os campos DE CLR e SP. Isso simplifica a integração de um idioma proprietário ao IDE do Visual Studio.  
  
 Quando o CLR DE chama o EE proprietária para avaliar uma expressão, o DE fornece EE com interfaces um SP e um objeto de associador. Assim, gravando um meio de mecanismo de depuração com base em CLR é necessário somente implementar as interfaces do avaliador de expressão apropriada; o CLR cuida de associação e o símbolo de tratamento para você.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)