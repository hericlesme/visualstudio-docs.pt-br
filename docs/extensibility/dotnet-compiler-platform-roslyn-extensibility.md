---
title: Plataforma do compilador .NET (&quot;Roslyn&quot;) extensibilidade | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab5a486866cb4bc97835a2977fec6e6eb6bc2820
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639894"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Plataforma do compilador .NET (&quot;Roslyn&quot;) extensibilidade
A missão de núcleo do .NET Compiler Platform ("Roslyn") está abrindo os compiladores c# e Visual Basic e permitindo que as ferramentas e os desenvolvedores compartilhem nos compiladores informações ricas têm sobre os programas. Ferramentas de análise de código melhorar a qualidade do código e geradores de auxílio na criação do aplicativo de código. Como as ferramentas ficam mais inteligentes, elas precisam de acesso a cada vez mais do que o conhecimento profundo do código que somente os compiladores podem ter. Em vez de ser tradutores opacos (no código-fonte e código de objeto-out), os compiladores Roslyn oferecem APIs que você pode usar para tarefas relacionadas ao código em seus aplicativos e ferramentas.  
  
 A melhor parte é que os compiladores Roslyn, suas APIs, exemplos e explicações passo a passo e as ferramentas criadas sobre essas APIs são todas totalmente de software livre no [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Vá para o site de OSS para saber mais e começar a trabalhar com o Roslyn. Você encontrará links para obter os mais recentes em C# e VB recursos que você pode usar como um usuário final, bem como links para começar a usar como um construtor de ferramenta aproveitando as APIs do Roslyn.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao analisadores Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)