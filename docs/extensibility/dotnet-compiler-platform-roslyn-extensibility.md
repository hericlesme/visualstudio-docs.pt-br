---
title: Plataforma de compilador .NET (&quot;Roslyn&quot;) extensibilidade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f9811440146e1d758158a64fd227ba0a2c2e1e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Plataforma de compilador .NET (&quot;Roslyn&quot;) extensibilidade
O objetivo principal da plataforma .NET do compilador ("Roslyn") é abrindo os compiladores c# e Visual Basic e permitindo que ferramentas e tem desenvolvedores compartilhem os compiladores de informações detalhadas sobre os programas. Ferramentas de análise de código melhorar a qualidade do código e geradores auxílio na construção de aplicativos de código. Medida ferramentas mais inteligentes, eles precisará de acesso para cada vez mais do que possuem somente compiladores conhecimento profundo de código. Em vez de ser tradutores opacos (código-fonte e código objeto), os compiladores do Roslyn oferecem APIs que você pode usar para tarefas relacionadas ao código em seus aplicativos e ferramentas.  
  
 O mais importante é que os compiladores do Roslyn, suas APIs, exemplos e explicações passo a passo e as ferramentas reais criadas sobre essas APIs são código-fonte aberto inteiramente em [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Vá para o site de OSS para saber mais e começar a trabalhar com Roslyn. Você encontrará links para obter o mais recente c# e VB recursos que você pode usar como um usuário final, bem como links para iniciar como um construtor ferramenta utilizando as APIs Roslyn.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao analisadores Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)