---
title: Plataforma de compilador .NET (&quot;Roslyn&quot;) extensibilidade | Microsoft Docs
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
ms.openlocfilehash: 09287c48285bfcdc32b1a7d558d44f9d212f1b41
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Plataforma de compilador .NET (&quot;Roslyn&quot;) extensibilidade
O objetivo principal da plataforma .NET do compilador ("Roslyn") é abrindo os compiladores c# e Visual Basic e permitindo que ferramentas e tem desenvolvedores compartilhem os compiladores de informações detalhadas sobre os programas. Ferramentas de análise de código melhorar a qualidade do código e geradores auxílio na construção de aplicativos de código. Medida ferramentas mais inteligentes, eles precisará de acesso para cada vez mais do que possuem somente compiladores conhecimento profundo de código. Em vez de ser tradutores opacos (código-fonte e código objeto), os compiladores do Roslyn oferecem APIs que você pode usar para tarefas relacionadas ao código em seus aplicativos e ferramentas.  
  
 O mais importante é que os compiladores do Roslyn, suas APIs, exemplos e explicações passo a passo e as ferramentas reais criadas sobre essas APIs são código-fonte aberto inteiramente em [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Vá para o site de OSS para saber mais e começar a trabalhar com Roslyn. Você encontrará links para obter o mais recente c# e VB recursos que você pode usar como um usuário final, bem como links para iniciar como um construtor ferramenta utilizando as APIs Roslyn.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao analisadores Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)