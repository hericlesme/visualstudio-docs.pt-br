---
title: "Introdução ao Roslyn analisadores | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec424f5e85f5bff9be5b276b3978b25dc3239fe5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introdução ao Roslyn analisadores
Com analisadores de ao vivo, com base em projeto de código no Visual Studio, os autores de API podem ser fornecidas a análise de código específicas de domínio como parte de seus pacotes NuGet.  Porque essas analisadores são alimentadas pela plataforma do compilador .NET (codinome "Roslyn"), eles podem produzir avisos em seu código conforme você digita, mesmo antes de terminar a linha (não mais aguardando para compilar seu código para descobrir problemas).  Analisadores também podem surgir uma correção automática de código por meio do prompt de lâmpada do Visual Studio para permitir que você limpar seu código imediatamente  
  
## <a name="getting-started"></a>Guia de Introdução  
 [Analisadores de código ao vivo Roslyn Introdução e instruções passo a passo](https://msdn.microsoft.com/en-us/magazine/dn879356.aspx)  
  
 [Adicionando código corrige passo a passo: Fornecer usuários correções para problemas de analisador](https://msdn.microsoft.com/en-us/magazine/dn904670.aspx)  
  
 [Introdução e instruções passo a passo de conversa de analisador do mundo Real](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Analisador de Roslyn mundo real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que você também pode assistir como um [falar](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Vários exemplos no github, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
  
 [Introdução e Tour de analisadores alguns falar](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)  
  
## <a name="other-resources"></a>Outros recursos  
 [Documentos mais no site do github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
  
 [Regras FxCop implementadas com Roslyn analisadores no github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)